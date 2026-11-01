# Developer Specification: Terms Acceptance Recording, Re-Acceptance Gate, and Version Archive

Document Path: [docs/platform-legal/acceptance-implementation.md](./acceptance-implementation.md)
Master Legal Directory: [docs/platform-legal/README.md](./README.md)
Related Documents:
- Terms and Conditions (Indonesian): [docs/platform-legal/terms-and-conditions.id.md](./terms-and-conditions.id.md)
- Terms and Conditions (English): [docs/platform-legal/terms-and-conditions.en.md](./terms-and-conditions.en.md)
- Table of Contents (Indonesian): [docs/platform-legal/TOC.id.md](./TOC.id.md)
- Table of Contents (English): [docs/platform-legal/TOC.en.md](./TOC.en.md)
- Internal Fact Sheet: [docs/platform-legal/fact-sheet.md](./fact-sheet.md)
- Clause-to-Function Mapping: [docs/platform-legal/clause-function-map.md](./clause-function-map.md)

## 1. Objective and Legal Evidentiary Requirements

To satisfy **Function 1 (Binding Contract)** and **Function 6 (Usable Evidence in a Dispute)** of the Terms and Conditions ([Article 2.3](./terms-and-conditions.en.md#23-electronic-acceptance-and-binding-effect), [Article 2.4](./terms-and-conditions.en.md#24-re-acceptance-upon-material-amendments), and [Article 19.1](./terms-and-conditions.en.md#191-admissibility-of-electronic-records-and-acceptance-logs)), the platform backend (`backend/dashboard`) must implement a tamper-evident electronic acceptance and version management subsystem that guarantees four core invariants:

1. **Per-User Acceptance Recording**: Every acceptance event must persist the **accepted version** (`terms_version`), **UTC timestamp** (`accepted_at`), **account identifier** (`user_id` and `username`), and **acceptance method** (`acceptance_method`), together with corroborating request metadata (`client_ip`, `user_agent`, `language`, and SHA-256 hashes of the accepted Markdown files).
2. **Mandatory Re-Acceptance When Terms Change**: Whenever a new Terms version is published with `require_reacceptance = true`, existing authenticated users whose `accepted_terms_version` does not match the active version must be gated from dashboard mutations and AI Agent deployments until they complete explicit re-acceptance.
3. **Permanent Retrievability of Past Versions**: Every historical version of [docs/platform-legal/terms-and-conditions.id.md](./terms-and-conditions.id.md) and [docs/platform-legal/terms-and-conditions.en.md](./terms-and-conditions.en.md) (along with Annexes A–F in `docs/platform-legal/annexes/`) must remain stored and retrievable by version identifier so that any acceptance record can be matched to the exact contract text that was in force at the timestamp of acceptance.
4. **Surviving Audit Trail**: Acceptance records must never be deleted by subscription termination or the 15-day post-suspension data purge (`BillingSuspendRetentionDays`).

---

## 2. Current Codebase Audit (`backend/dashboard`)

| Component | File Path | Current Behavior | Gap to Close |
| :--- | :--- | :--- | :--- |
| **Registration UI (Step 3)** | [templates/register.html](../../templates/register.html) & [assets/js/register.js](../../assets/js/register.js) | Renders `<input type="checkbox" id="terms" name="terms" required>` with placeholder `href="#"` links and validates `termsCheckbox.checked` client-side only. | Must link to the live Terms route, display the active `terms_version`, and send `terms_accepted: true`, `terms_version`, and `terms_language` in the `POST /api/v1/register/complete` JSON payload. |
| **Registration Handler & Usecase** | [internal/interface/api/v1/handler/register.go](../../internal/interface/api/v1/handler/register.go) & [internal/usecase/register/complete.go](../../internal/usecase/register/complete.go) | `CompleteRegistrationRequest` binds `session_id`, `business_name`, `full_name`, `username`, and `password`. Does not validate or store Terms acceptance. | Must require `terms_accepted == true` and a valid `terms_version`, write an append-only record to `terms_acceptances`, and populate `AcceptedTermsVersion`, `AcceptedTermsAt`, and `AcceptedTermsMethod` on `UserInfo`. |
| **Google OAuth Login** | [internal/interface/api/v1/handler/login.go](../../internal/interface/api/v1/handler/login.go) & [internal/usecase/login/login.go](../../internal/usecase/login/login.go) | `POST /api/v1/login/google` auto-creates a `UserInfo` record on first sign-in without recording Terms acceptance. | Newly created or existing users whose `AcceptedTermsVersion` is empty or outdated must be flagged with `terms_acceptance_required: true` and prompted via the re-acceptance modal before using the dashboard. |
| **User Domain Entity** | [internal/domain/user/user.go](../../internal/domain/user/user.go) | `UserInfo` stores `ID`, `Username`, `Email`, `PhoneNumber`, `FullName`, `BusinessName`, `Password`, `Roles`, `IsBanned`, `CreatedAt`, `UpdatedAt`. | Add `AcceptedTermsVersion string`, `AcceptedTermsAt *time.Time`, and `AcceptedTermsMethod string` to `UserInfo`. |

---

## 3. Database Schema Design

### 3.1. Collection: `terms_versions` (Immutable Version Archive)

Stores every published version of the Terms and Conditions so that historical versions are permanently retrievable.

```go
package legal

import "time"

type TermsVersion struct {
	ID                  string    `bson:"_id,omitempty" json:"id"`
	Version             string    `bson:"version" json:"version"`                           // Unique semantic version, e.g., "1.0", "1.1", "2.0"
	EffectiveDate       time.Time `bson:"effective_date" json:"effective_date"`             // Effective date in UTC
	PublishedAt         time.Time `bson:"published_at" json:"published_at"`                 // Publication timestamp in UTC
	IsCurrent           bool      `bson:"is_current" json:"is_current"`                     // True for the single currently active version
	RequireReacceptance bool      `bson:"require_reacceptance" json:"require_reacceptance"` // If true, users on older versions must re-accept
	SummaryID           string    `bson:"summary_id" json:"summary_id"`                     // Summary of changes (Indonesian)
	SummaryEN           string    `bson:"summary_en" json:"summary_en"`                     // Summary of changes (English)
	ContentIDMarkdown   string    `bson:"content_id_md" json:"content_id_md"`               // Full immutable Markdown text (Indonesian)
	ContentENMarkdown   string    `bson:"content_en_md" json:"content_en_md"`               // Full immutable Markdown text (English)
	SHA256ID            string    `bson:"sha256_id" json:"sha256_id"`                       // Hex SHA-256 digest of ContentIDMarkdown
	SHA256EN            string    `bson:"sha256_en" json:"sha256_en"`                       // Hex SHA-256 digest of ContentENMarkdown
}
```

**Required Indexes on `terms_versions`**:
1. `{ "version": 1 }` — `unique: true`
2. `{ "is_current": 1 }` — partial or standard index for fast active-version lookup
3. `{ "published_at": -1 }` — for chronological listing of past versions

### 3.2. Collection: `terms_acceptances` (Append-Only Evidentiary Log)

Records each acceptance or re-acceptance action by a Customer account. Documents in this collection are **append-only** and must never be modified or deleted.

```go
package legal

import "time"

type AcceptanceMethod string

const (
	AcceptanceMethodRegisterCheckbox   AcceptanceMethod = "register_checkbox"
	AcceptanceMethodGoogleOAuthPrompt  AcceptanceMethod = "google_oauth_prompt"
	AcceptanceMethodReacceptanceModal  AcceptanceMethod = "reacceptance_modal"
	AcceptanceMethodCheckoutClickwrap  AcceptanceMethod = "checkout_clickwrap"
)

type TermsAcceptance struct {
	ID               string           `bson:"_id,omitempty" json:"id"`
	UserID           string           `bson:"user_id" json:"user_id"`                   // Account identifier (UserInfo.ID hex)
	Username         string           `bson:"username" json:"username"`                 // Account username at time of acceptance
	EmailSnapshot    string           `bson:"email_snapshot" json:"email_snapshot"`     // Registered email at time of acceptance
	TermsVersion     string           `bson:"terms_version" json:"terms_version"`       // Accepted version (e.g., "1.0")
	ContentSHA256ID  string           `bson:"content_sha256_id" json:"content_sha256_id"`
	ContentSHA256EN  string           `bson:"content_sha256_en" json:"content_sha256_en"`
	AcceptedAt       time.Time        `bson:"accepted_at" json:"accepted_at"`           // Server-generated UTC timestamp
	AcceptanceMethod AcceptanceMethod `bson:"acceptance_method" json:"acceptance_method"`
	Language         string           `bson:"language" json:"language"`                 // UI language when accepted ("id" or "en")
	ClientIP         string           `bson:"client_ip" json:"client_ip"`               // Normalized client IP address
	UserAgent        string           `bson:"user_agent" json:"user_agent"`             // Browser User-Agent header (truncated to 512 chars)
	SessionID        string           `bson:"session_id,omitempty" json:"session_id,omitempty"` // Registration session ID or auth token JTI
}
```

**Required Indexes on `terms_acceptances`**:
1. `{ "user_id": 1, "accepted_at": -1 }` — fast lookup of a user's complete acceptance history
2. `{ "user_id": 1, "terms_version": 1 }` — fast verification of whether a user accepted a specific version
3. `{ "terms_version": 1, "accepted_at": -1 }` — compliance auditing by version

### 3.3. Denormalized Fields on `UserInfo` ([internal/domain/user/user.go](../../internal/domain/user/user.go))

Add the following fields to `UserInfo` so authentication and middleware checks can verify acceptance status in O(1) without an extra collection join on every request:

```go
AcceptedTermsVersion string     `bson:"accepted_terms_version,omitempty" json:"accepted_terms_version,omitempty"`
AcceptedTermsAt      *time.Time `bson:"accepted_terms_at,omitempty" json:"accepted_terms_at,omitempty"`
AcceptedTermsMethod  string     `bson:"accepted_terms_method,omitempty" json:"accepted_terms_method,omitempty"`
```

---

## 4. Startup Seeding and Version Archival Lifecycle

1. **Automatic Version Sync on Startup**:
   - On server startup, a seeder reads [docs/platform-legal/terms-and-conditions.id.md](./terms-and-conditions.id.md) and [docs/platform-legal/terms-and-conditions.en.md](./terms-and-conditions.en.md) alongside the configured `LEGAL_TERMS_VERSION` (e.g., `"1.0"`) and `LEGAL_TERMS_EFFECTIVE_DATE`.
   - It computes `sha256(content_id_md)` and `sha256(content_en_md)`.
   - If `terms_versions` does not yet contain `version == LEGAL_TERMS_VERSION`, the seeder:
     1. Sets `is_current = false` on all existing `terms_versions` documents.
     2. Inserts the new `TermsVersion` document with `is_current = true` and `require_reacceptance = true`.
   - If `version == LEGAL_TERMS_VERSION` already exists in `terms_versions`, the seeder verifies that the stored SHA-256 digests match the files on disk. If the Markdown content changed without bumping `LEGAL_TERMS_VERSION`, startup logs a critical warning or fails fast so developers never silently mutate an already-accepted contract version without incrementing the version identifier.

---

## 5. API Endpoints and Implementation Flows

### 5.1. Public Version Retrieval Endpoints (Keeping Past Versions Retrievable)

1. **`GET /api/v1/legal/terms/current`**
   - **Auth**: Public.
   - **Response**: Returns the active `TermsVersion` (`version`, `effective_date`, `published_at`, `sha256_id`, `sha256_en`, `content_id_md`, `content_en_md`).
2. **`GET /api/v1/legal/terms/versions`**
   - **Auth**: Public.
   - **Response**: Returns metadata list of all current and historical versions ordered by `published_at DESC` (`version`, `effective_date`, `published_at`, `is_current`, `summary_id`, `summary_en`, `sha256_id`, `sha256_en`).
3. **`GET /api/v1/legal/terms/versions/:version`**
   - **Auth**: Public.
   - **Response**: Returns the full `TermsVersion` document (including `content_id_md` and `content_en_md`) for the requested historical `:version`.

### 5.2. Flow 1 — Standard Registration Acceptance (`POST /api/v1/register/complete`)

1. **Request Payload ([internal/interface/api/v1/handler/register.go](../../internal/interface/api/v1/handler/register.go))**:
   Extend `CompleteRegistrationRequest`:
   ```go
   type CompleteRegistrationRequest struct {
       SessionID     string `json:"session_id" binding:"required"`
       BusinessName  string `json:"business_name" binding:"required"`
       FullName      string `json:"full_name" binding:"required"`
       Username      string `json:"username" binding:"required"`
       Password      string `json:"password" binding:"required"`
       TermsAccepted bool   `json:"terms_accepted" binding:"required"`
       TermsVersion  string `json:"terms_version" binding:"required"`
       TermsLanguage string `json:"terms_language"`
   }
   ```
2. **Usecase Validation ([internal/usecase/register/complete.go](../../internal/usecase/register/complete.go))**:
   - Reject with `400 Bad Request` (`ErrTermsNotAccepted`) if `!req.TermsAccepted`.
   - Fetch the active `TermsVersion` (`is_current == true`). Reject with `409 Conflict` (`ErrTermsVersionOutdated`) if `req.TermsVersion != currentTerms.Version` so the client refreshes and displays the latest contract text.
   - Generate `now := time.Now().UTC()`.
   - Set on `UserInfo`:
     - `AcceptedTermsVersion = currentTerms.Version`
     - `AcceptedTermsAt = &now`
     - `AcceptedTermsMethod = string(legal.AcceptanceMethodRegisterCheckbox)`
   - Insert `TermsAcceptance` into `terms_acceptances` with:
     - `UserID = createdUser.ID`
     - `Username = createdUser.Username`
     - `EmailSnapshot = createdUser.Email`
     - `TermsVersion = currentTerms.Version`
     - `ContentSHA256ID = currentTerms.SHA256ID`
     - `ContentSHA256EN = currentTerms.SHA256EN`
     - `AcceptedAt = now`
     - `AcceptanceMethod = legal.AcceptanceMethodRegisterCheckbox`
     - `Language = normalizedLanguage(req.TermsLanguage)` (`"id"` or `"en"`)
     - `ClientIP = clientIP`
     - `UserAgent = truncateUserAgent(userAgent)`
     - `SessionID = req.SessionID`

### 5.3. Flow 2 — Re-Acceptance When Terms Change & Google OAuth First Sign-In (`POST /api/v1/legal/terms/accept`)

1. **Detection During Login & Session Refresh**:
   - In `POST /api/v1/login`, `POST /api/v1/login/verify-otp`, `POST /api/v1/login/google`, and `GET /api/v1/me`:
   - Compare `user.AcceptedTermsVersion` against the active `TermsVersion.Version`.
   - Include in the response payload:
     ```json
     {
       "terms_status": {
         "accepted_version": "1.0",
         "current_version": "1.1",
         "reacceptance_required": true
       }
     }
     ```
2. **Backend Enforcement Middleware (`RequireCurrentTermsAcceptance`)**:
   - Applied to all authenticated customer API routes (`/api/v1/builder/*`, `/api/v1/subscription/*`, `/api/v1/wallet/*`, `/api/v1/profile/*`), while exempting:
     - `GET /api/v1/me`
     - `GET /api/v1/legal/terms/*`
     - `POST /api/v1/legal/terms/accept`
     - `POST /api/v1/logout`
   - If the authenticated user is not an admin and `user.AcceptedTermsVersion != currentActiveTermsVersion` (where `currentActiveTerms.RequireReacceptance == true`), the middleware returns `428 Precondition Required` (or `403 Forbidden`) with code `"TERMS_REACCEPTANCE_REQUIRED"` and `current_version`.
3. **Acceptance / Re-Acceptance Endpoint (`POST /api/v1/legal/terms/accept`)**:
   - **Auth**: Requires valid authenticated user access token.
   - **Request Body**:
     ```json
     {
       "terms_version": "1.1",
       "accepted": true,
       "language": "id",
       "acceptance_context": "reacceptance_modal"
     }
     ```
   - **Execution**:
     1. Validate `accepted == true` and verify `terms_version == currentTerms.Version`.
     2. Determine `AcceptanceMethod`:
        - If `user.AcceptedTermsVersion == ""` (e.g., first-time Google OAuth user completing the prompt), record `AcceptanceMethodGoogleOAuthPrompt`.
        - Otherwise, record `AcceptanceMethodReacceptanceModal`.
     3. Insert the new immutable `TermsAcceptance` document into `terms_acceptances` with `UserID`, `Username`, `EmailSnapshot`, `TermsVersion`, `ContentSHA256ID`, `ContentSHA256EN`, `AcceptedAt = time.Now().UTC()`, `AcceptanceMethod`, `Language`, `ClientIP`, `UserAgent`, and token `JTI`.
     4. Update `UserInfo` (`AcceptedTermsVersion`, `AcceptedTermsAt`, `AcceptedTermsMethod`).
     5. Return `200 OK` with the recorded acceptance receipt (`id`, `user_id`, `terms_version`, `accepted_at`, `acceptance_method`).

### 5.4. Flow 3 — Admin Dispute Evidence Query (`GET /api/v1/admin/users/:id/terms-acceptances`)

- **Auth**: Admin / Superadmin only.
- **Purpose**: Produces a complete, court-ready JSON report of a user's Terms acceptance history for dispute resolution under [Article 19.1](./terms-and-conditions.en.md#191-admissibility-of-electronic-records-and-acceptance-logs).
- **Response**: Returns all `terms_acceptances` records for `:id` ordered by `accepted_at DESC`, paired with the corresponding `terms_versions` metadata (`effective_date`, `sha256_id`, `sha256_en`).

---

## 6. Verification Checklist for Developers

1. **Unit & Integration Tests**:
   - Verify `POST /api/v1/register/complete` fails with `400` when `terms_accepted` is `false` or omitted, and fails with `409` when `terms_version` does not match the current active version.
   - Verify successful registration creates both the `UserInfo` fields and an entry in `terms_acceptances` with `acceptance_method = "register_checkbox"`, non-empty `user_id`, `terms_version`, and UTC `accepted_at`.
   - Verify a user created via `POST /api/v1/login/google` has `reacceptance_required = true` until `POST /api/v1/legal/terms/accept` is called, and is blocked by `RequireCurrentTermsAcceptance` from deploying AI Agents or creating invoices before accepting.
   - Verify publishing version `"1.1"` with `require_reacceptance = true` immediately gates a user who previously accepted `"1.0"`, and that after calling `POST /api/v1/legal/terms/accept` for `"1.1"`, both `"1.0"` and `"1.1"` records exist in `terms_acceptances` and both `"1.0"` and `"1.1"` contract texts remain retrievable via `GET /api/v1/legal/terms/versions/:version`.
   - Verify the subscription purge job (`purgeExpiredSuspended` in [internal/usecase/payment/scheduler.go](../../internal/usecase/payment/scheduler.go)) never deletes documents from `terms_versions` or `terms_acceptances`.
