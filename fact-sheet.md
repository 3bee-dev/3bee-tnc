# Internal Legal Fact Sheet: 3Bee AI Agent Builder Platform

Document Path: [fact-sheet.md](./fact-sheet.md)
Master Legal Directory: [README.md](./README.md)
Related Documents:
- Terms and Conditions (Indonesian): [terms-and-conditions.id.md](./terms-and-conditions.id.md)
- Terms and Conditions (English): [terms-and-conditions.en.md](./terms-and-conditions.en.md)
- Table of Contents (Indonesian): [TOC.id.md](./TOC.id.md)
- Table of Contents (English): [TOC.en.md](./TOC.en.md)
- Clause-to-Function Mapping: [clause-function-map.md](./clause-function-map.md)
- Developer Acceptance Specification: [acceptance-implementation.md](./acceptance-implementation.md)

## 1. Document Purpose and Scope

This internal fact sheet records the verified technical, operational, commercial, and data-processing facts of the 3Bee platform across its three repositories (`backend/dashboard`, `agent`, and `landing-page`). It serves as the factual baseline for drafting and reviewing:
- Customer-facing Terms and Conditions: [terms-and-conditions.id.md](./terms-and-conditions.id.md) and [terms-and-conditions.en.md](./terms-and-conditions.en.md)
- Customer-facing Table of Contents: [TOC.id.md](./TOC.id.md) and [TOC.en.md](./TOC.en.md)
- Standalone Annexes / Lampiran (`Annex A` through `Annex F`):
  - [annexes/annex-a-subscription-plans-quotas-credits.id.md](./annexes/annex-a-subscription-plans-quotas-credits.id.md) | [annexes/annex-a-subscription-plans-quotas-credits.en.md](./annexes/annex-a-subscription-plans-quotas-credits.en.md)
  - [annexes/annex-b-acceptable-use-and-uploads.id.md](./annexes/annex-b-acceptable-use-and-uploads.id.md) | [annexes/annex-b-acceptable-use-and-uploads.en.md](./annexes/annex-b-acceptable-use-and-uploads.en.md)
  - [annexes/annex-c-data-processing-and-retention.id.md](./annexes/annex-c-data-processing-and-retention.id.md) | [annexes/annex-c-data-processing-and-retention.en.md](./annexes/annex-c-data-processing-and-retention.en.md)
  - [annexes/annex-d-service-level-and-support.id.md](./annexes/annex-d-service-level-and-support.id.md) | [annexes/annex-d-service-level-and-support.en.md](./annexes/annex-d-service-level-and-support.en.md)
  - [annexes/annex-e-third-party-channels-and-widget.id.md](./annexes/annex-e-third-party-channels-and-widget.id.md) | [annexes/annex-e-third-party-channels-and-widget.en.md](./annexes/annex-e-third-party-channels-and-widget.en.md)
  - [annexes/annex-f-consumer-facing-terms.id.md](./annexes/annex-f-consumer-facing-terms.id.md) | [annexes/annex-f-consumer-facing-terms.en.md](./annexes/annex-f-consumer-facing-terms.en.md)
- Internal Clause-to-Function Mapping: [clause-function-map.md](./clause-function-map.md)
- Developer Acceptance Specification: [acceptance-implementation.md](./acceptance-implementation.md)

Customer-facing documents must never expose internal technology stack details, database collection names, environment variables, framework names, or vendor names (other than customer-facing channels WhatsApp and Telegram). All unconfirmed corporate, financial, or legal policy parameters must remain bracketed placeholders (`[...]`) or lawyer decision markers (`[LAWYER DECISION: ...]`).

---

## 2. Corporate Identity and Brand Facts

1. **Brand Name**: 3Bee (`3Bee AI Agent Builder Platform`).
2. **Display Entity Name on Landing Page**: `PT 3Bee Indonesia` (copyright notice `© 2026 3bee (PT 3Bee Indonesia)`).
3. **Display Address on Landing Page**: `Jl. Sutomo No 9, Jakarta, Indonesia`.
4. **Staging / App Domains in Configuration**: `3bee.umkmate.com`, `3bee.tech`, `3bee.dev`.
5. **Unverified Legal Entity Details (Must Use Placeholders in Terms)**:
   - `[COMPANY LEGAL NAME]`
   - `[COMPANY REGISTRATION NUMBER / NIB]`
   - `[REGISTERED ADDRESS]`
   - `[LEGAL NOTICE EMAIL]`
   - `[SUPPORT EMAIL]`
   - `[SUPPORT WHATSAPP NUMBER]`
   - `[SUPPORT TELEGRAM HANDLE]`
   - `[EFFECTIVE DATE]`

---

## 3. Platform Architecture and Service Offerings

1. **Core Service**: A no-code Software-as-a-Service (SaaS) platform that enables business customers to build, train, deploy, and manage conversational AI Agents, product catalogs, workflow automation, and AI-powered Virtual Try-On experiences across web and messaging channels.
2. **Two-Dashboard Operational Model**:
   - **Main Platform Dashboard (`3Bee Dashboard`)**: Used by the Customer (Tenant) to register and verify their account, subscribe to a package, top up Credit Balance, create AI Agent instances, run guided deployment to a custom subdomain, configure WhatsApp and Telegram connections, configure the embeddable Web Widget, test prompts and sample products in the Playground, select AI Model tiers, configure per-session visitor limits, monitor Visitor Analytics, and manage billing and profile security.
   - **Per-Agent Workspace (`Agent Dashboard`)**: Provisioned per deployed AI Agent on a dedicated subdomain. Accessed by the Customer via Master Account credentials or one-click Single Sign-On (SSO) from the Main Platform Dashboard, and by team members via Operator Accounts created by the Master Account. Used to manage the Product Catalog, Knowledge Base documents, Virtual Try-On product bindings and reference photos, AI Instructions (Persona, Roleplay, Core Instructions, Templates, Skill Files), and store branding (brand name and logo).
3. **Supported Customer-Facing Channels**:
   - **Dedicated Web App**: Hosted storefront and chat interface on a Customer-chosen subdomain (`<subdomain>.[PLATFORM ROOT DOMAIN]`).
   - **Embeddable Web Widget**: Floating chat button and iframe widget embeddable on the Customer's own external websites, restricted via `Content-Security-Policy: frame-ancestors` to up to 10 Customer-authorized HTTPS domain origins (`MaxAllowedOrigins = 10`; no wildcards, no raw IP addresses, no `localhost`). See [Annex E (EN)](./annexes/annex-e-third-party-channels-and-widget.en.md) / [Lampiran E (ID)](./annexes/annex-e-third-party-channels-and-widget.id.md).
   - **WhatsApp Business**: Connected using Customer-supplied Meta WhatsApp Cloud API credentials (`whatsapp_token`, `phone_number_id`, `whatsapp_business_account_id`, `whatsapp_verify_token`).
   - **Telegram**: Connected using Customer-supplied Telegram Bot API token (`telegram_token`).

---

## 4. Account Registration, Authentication, and Access Control

1. **Self-Service Registration Flow (3 Steps)**:
   - **Step 1**: Customer submits email address, phone number (`^\+?[0-9]{8,15}$`), and passes a bot-verification challenge (Cloudflare Turnstile). System sends a 6-digit numeric OTP to the email address (default TTL: 300 seconds / 5 minutes; maximum 5 verification attempts; 60-second resend cooldown; registration session TTL: 900 seconds / 15 minutes).
   - **Step 2**: Customer verifies the 6-digit email OTP code.
   - **Step 3**: Customer submits Business Name, Full Name, Username (3–30 alphanumeric characters), and Password (minimum 8 characters containing at least one letter and one digit), and checks the Terms & Conditions and Privacy Policy acceptance checkbox.
2. **Sign-In Methods**:
   - Identifier (username or email) + password + bot-verification challenge.
   - Google Identity Services OAuth sign-in (`POST /api/v1/login/google`), which can auto-create an account on first valid sign-in if none exists.
3. **Two-Step Login Verification and Trusted Devices**:
   - Password sign-ins (and admin sign-ins) support email OTP challenge verification (`LOGIN_OTP_MODE`, defaulting to `newdevice` for users and `always` for admins).
   - Upon completing login OTP verification, a trusted device token is stored via cookie for 30 days.
4. **Brute-Force and Session Controls**:
   - Per-client login failure limit: 10 failed attempts for a given identifier + client IP (full IPv4 or IPv6 `/64`) within a 15-minute window locks that client for 15 minutes (`LoginFailureLimit = 10`, `LoginFailureWindow = 15m`).
   - Access tokens (JWT) expire in 15 minutes (`900s`); refresh tokens (256-bit random token stored as SHA-256 hash in DB, sent in `HttpOnly`, `SameSite=Strict` cookie) expire in 7 days (`604800s`).
   - Password change or password reset (via 8-digit email reset code) stamps `PasswordChangedAt`, immediately invalidating all refresh tokens issued prior to that timestamp.
5. **Agent Dashboard Roles**:
   - **Master Account**: Configured during AI Agent deployment; has full administrative rights in the Agent Dashboard, including creating/deleting Operator Accounts. Master password is encrypted at rest using AES-256-GCM when `MASTER_PASSWORD_ENCRYPTION_KEY` is configured.
   - **Operator Account**: Standard team account inside the Agent Dashboard for daily catalog and knowledge-base operations; cannot manage other users.

---

## 5. Subscriptions, Quotas, AI Models, Metering, and Billing

1. **Plans and Billing Cycles**:
   - Subscription plans (`Package`) are managed in the platform catalog with Monthly (`monthly`) and Annual (`annual`) billing cycles. See [Annex A (EN)](./annexes/annex-a-subscription-plans-quotas-credits.en.md) / [Lampiran A (ID)](./annexes/annex-a-subscription-plans-quotas-credits.id.md).
   - Annual pricing uses either an explicit `price_annual` override on the package or `price_monthly * 12 * (100 - annual_discount_pct) / 100`.
   - Deactivated packages (`active = false`) are soft-deactivated, never hard-deleted.
   - **Anti-Drift Snapshot Rule**: Active subscribers run each billing period on a frozen `QuotaSnapshot` and `LastPaidAmount` / `LastPaidCycle`. Catalog price or quota changes by platform administrators never alter an already-issued invoice or a running period; if a package is deactivated, existing subscribers can continue renewing at their frozen `LastPaidAmount` for the same billing cycle.
2. **Currency and Taxes**:
   - All catalog prices, invoices, and Credit top-ups are denominated and settled in whole Indonesian Rupiah (`IDR`), inclusive of applicable taxes (`Semua harga sudah termasuk pajak`).
   - When the user interface is set to English, prices are displayed with an approximate `USD` equivalent calculated from a periodic exchange-rate feed (`open.er-api.com`, refreshed every 6 hours, fallback `18,000 IDR = 1 USD`), with an explicit notice that billing is settled in `IDR`.
3. **Three-Stage Quota and Credit Consumption Waterfall**:
   - Metered AI actions (`respon_chat` for AI chat responses and `respon_vto` for Virtual Try-On image generations) are consumed atomically in the following strict order:
     1. **Stage 1 — Monthly Package Quota (`Quota`)**: Deducts `1 * QuotaMultiplier` units from the period's `monthly_quota_chat_response` or `monthly_quota_tryon` counter (default model multiplier = `1`; higher-tier Package Models may apply an integer multiplier `>= 1`).
     2. **Stage 2 — Monthly Credit Pool (`Credit Pool`)**: Once Stage 1 is exhausted, deducts the action's credit tariff (`UnitPrice`) from the period's `monthly_ai_credit` pool.
     3. **Stage 3 — Credit Balance / Wallet (`Saldo Credit`)**: Once Stage 2 is exhausted, deducts the action's credit tariff (`UnitPrice`) from the Customer's topped-up Credit Balance (`1 Credit = 1 IDR`), **unless** the Customer has enabled the `WalletOverageDisabled` toggle, which stops consumption after Stage 2.
     4. **Fail-Closed Rejection**: If all enabled stages have insufficient quota/balance, the action is rejected (`ErrQuotaExhausted`). Quota exhaustion does not suspend the subscription or delete data.
   - Default AI model credit tariffs seeded in the database (`credit_prices`): `250` Credits per chat response (`DefaultCreditChat = 250`) and `2,000` Credits per Virtual Try-On (`DefaultCreditVTO = 2000`), subject to admin configuration up to `1,000,000` Credits per action and per-model tariffs (`ModelCreditPrice`).
   - Failed actions that are reverted (`/api/v1/agent/usage/revert`) restore the exact consumed quota units or credit balance once (`Reverted` / `RevertDone` idempotency flags).
4. **Knowledge Base Slot Metering**:
   - Each package specifies a `knowledge_base_limit` (maximum knowledge base documents across the tenant's active AI Agents).
   - Uploading a document claims a slot (`kb_upload`); deleting a document releases the slot (`kb-release`).
   - Switching or re-subscribing to a plan with a lower `knowledge_base_limit` than the tenant's currently stored document count is blocked (`kbgate`) until the Customer deletes excess documents.
5. **Visitor Session Limits**:
   - Customers can configure per-visitor-session rate limits for each AI Agent (`SessionLimits`): `1` to `10,000` requests per `1` to `4` minute window for Chat and/or Virtual Try-On, or leave them `Unlimited`.
6. **Invoicing, Prepayment, and Plan Switching**:
   - **Initial Activation (`pending_activation`)**: A new subscription starts in `pending_activation` with deployment and quota locked until the first invoice settles. If the first invoice expires unpaid and remains unsettled after the retention window, the abandoned subscription is terminated (`TerminateAbandonedGenesis`) so the Customer can re-subscribe.
   - **Renewal Invoicing (`H-2`)**: Renewal invoices (`SUB-...`) are generated automatically 2 days before `CurrentPeriodEnd` (`NextInvoiceDate = CurrentPeriodEnd - 2 days`), due on `CurrentPeriodEnd`.
   - **Early Renewal (`Bayar Periode Depan` / Pay-Next)**: An active subscriber may prepay the single next period on demand. For annual subscriptions, early payment opens 1 calendar month before `CurrentPeriodEnd`. Once the next period is prepaid, it rolls over automatically at `CurrentPeriodEnd`.
   - **Plan Switching (`Ubah Paket`)**: An active subscriber (whose next period is not yet prepaid) may schedule a package and/or billing cycle change for the next period (`PendingPackageID`, `PendingBillingCycle`), or pay immediately for the new plan (`Bayar Paket Baru`). The new plan's limits and cycle take effect at the period transition (`AdvancePeriod`), never mid-period. If a newly applied plan has a lower `MaxActiveAINodes` limit or disables a previously enabled channel (WhatsApp/Telegram), excess live AI Agents are automatically stopped into `PENDING` status (with 15-day data retention) and disabled channels are turned off.
7. **Credit Balance Top-Ups**:
   - Customers with an active subscription may purchase Credit Balance top-ups (`DEP-...`), minimum `10,000` Credits/IDR (`WALLET_TOPUP_MIN`), maximum `100,000,000` Credits/IDR (`WALLET_TOPUP_MAX`), with at most `3` concurrent pending top-up demands per Customer.
   - Top-up Credits are recorded in an append-only double-entry ledger (`wallet_ledger`) and do not expire at the end of a monthly/annual billing period.
8. **Payment Gateway, Review States, and Refunds**:
   - Payments are processed via Midtrans Snap and Core API (supporting Virtual Accounts, QRIS, e-wallets such as GoPay/DANA/ShopeePay, cards, etc.).
   - Webhook notifications are verified using constant-time SHA-512 signature comparison and re-verified against the gateway's authoritative `GET /v2/{order_id}/status` endpoint before any state mutation.
   - Discrepant or anomalous transactions (`amount_mismatch`, `settlement_unconfirmed`, `fraud_challenge`, `post_settlement_status`, `apply_failed`, `moving_timeout`, `fallback_exhausted`) transition to `needs_review` (`Perlu Ditinjau`). While an invoice is in `needs_review`, automated overdue service suspension and data deletion are fenced (held) until a platform administrator executes `Konfirmasi Manual` (manual confirmation) or `Reject Pembayaran` (rejection/refund flagging).
   - Duplicate or orphaned settled charges are flagged in `refund_transactions`. The platform does not perform automated self-service refunds; refunds are handled manually by administrators via email according to `[REFUND POLICY]`.

---

## 6. Overdue Ladder, Suspension, Cancellation, and Data Retention Lifecycle

1. **Grace Period (`grace`)**:
   - Trigger: Renewal invoice remains `pending` past its `DueDate` (`CurrentPeriodEnd`).
   - Duration: `BillingGracePeriodDays` (default `3` days; use `[GRACE PERIOD DAYS]` if policy may vary).
   - Effect: Deployed AI Agents **remain live and running**; new AI Agent creation/deployment is blocked; daily payment reminder emails (throttled to max 1 per 24 hours) and a grace-start notification (stating the grace deadline and data deletion deadline) are sent.
2. **Billing Suspension (`suspended`)**:
   - Trigger: Invoice remains unpaid after the Grace Period expires (and no invoice is in `needs_review`).
   - Effect: All live AI Agents of the Customer are stopped (`stopDeployedInfrastructure`: compute container and custom subdomain DNS records removed), and each service row is marked `SUSPENDED` (`reason = billing`) with a data-deletion deadline (`PurgeAfterAt = SuspendedAt + 15 days`).
   - Retention Window: `BillingSuspendRetentionDays` (default `15` days). During this 15-day window, the dedicated per-agent database (catalog, knowledge base documents, Virtual Try-On configurations, instructions, branding) and builder configurations are preserved intact. Paying the overdue invoice during `grace` or `suspended` reactivates the subscription and restores stopped AI Agents.
3. **Voluntary Subscription Cancellation (`CancelAtPeriodEnd`)**:
   - Trigger: Customer submits cancellation request verified by account password, cancellation reason (1–500 runes), and exact confirmation phrase.
   - Effect: Subscription remains `active` until `CurrentPeriodEnd` (and Customer may undo cancellation via `Lanjutkan Langganan` at any time before `CurrentPeriodEnd`). No renewal invoice is generated.
   - End of Paid Period: At `CurrentPeriodEnd`, live AI Agents stop immediately **without a Grace Period**, the subscription transitions directly to `suspended`, and the 15-day data retention window begins.
4. **Permanent Data Deletion (`terminated`)**:
   - Trigger: Subscription remains `suspended` for more than `15` days (`BillingSuspendRetentionDays`), verified with a 5-minute recent-payment guard and `needs_review` fence.
   - What is Deleted: Each AI Agent's dedicated MongoDB database (`<username>-<serviceID>`) is dropped, knowledge-base slot counters are reset, raw session tracker reports and per-visitor day marks are purged, builder service rows are deleted, and leftover pending invoices are marked `expired`. The subscription status is set to `terminated`.
   - What is Retained: The Customer's user account (`UserInfo`), Credit Balance (`wallet_balances` and `wallet_ledger`), and historical invoices/payment records are **never deleted** by the subscription purge, allowing the Customer to sign in and start a new subscription in the future.
5. **Per-Agent Retention for Active Subscribers (`PHASE 34`)**:
   - When an individual AI Agent of an active subscriber is stopped into `PENDING` (due to a package downgrade exceeding `MaxActiveAINodes`) or `SUSPENDED` (`SuspendReasonAdmin` or `SuspendReasonDowngrade`), its dedicated agent database is retained for `15` days (`PurgeAfterAt`). If not resumed within 15 days, the dedicated agent database and raw tracker data are dropped (`ResetControlPanelServiceData`), while the builder row itself (service name, subdomain setting, master credentials, channel tokens) is kept in a "not deployed" state.

---

## 7. AI Functionality, Guardrails, and Output Limitations

1. **Probabilistic Generation**:
   - AI chat replies, product recommendations, translations, catalog extractions, document OCR/parsing, and Virtual Try-On images are generated by third-party Large Language Models (LLMs) and multimodal vision/image models. Outputs are probabilistic and may contain inaccuracies, hallucinations, or visual artifacts.
2. **Built-In Virtual Try-On Disclaimer**:
   - Both the landing page (`id.ts` / `en.ts`) and the deployed agent (`constants.py`: `TRYON_DISCLAIMER`) display the following mandatory disclaimer on Virtual Try-On outputs:
     > "Virtual try-on is an AI-generated preview and may not be 100% accurate. It is intended for illustration/preview purposes only and is not a guarantee of the actual product's appearance or fit."
   - Virtual Try-On supports watches (with browser camera palm detection or photo upload), fashion/apparel, furniture (with room photo area marking and placement instructions), and universal accessories, subject to a 30-second per-sender cooldown (`TRYON_COOLDOWN_SECONDS = 30`) and 300-second generation timeout.
3. **Safety and Upload Guardrails**:
   - See [Annex B (EN)](./annexes/annex-b-acceptable-use-and-uploads.en.md) / [Lampiran B (ID)](./annexes/annex-b-acceptable-use-and-uploads.id.md).
   - **Prompt-Injection Guardrail**: Every chat turn passes through a two-tier regex detector (`PROMPT_INJECTION_PATTERNS` + corroborated `PROMPT_INJECTION_PATTERNS_SOFT`) and an independent safeguard LLM classifier (`llm_judge`) before retrieval or tool execution. Unsafe inputs are blocked with a polite refusal message.
   - **Out-of-Scope Filter**: Requests asking the shopping/receptionist agent to write/debug software code (`OUT_OF_SCOPE_PATTERNS`) are declined or rewritten by an independent scope-filter LLM call.
   - **Vision Guardrail for Virtual Try-On**: Customer-uploaded try-on photos are evaluated by an independent safeguard vision model (`vision_guardrail`) for category suitability before image generation runs.
   - **Document Upload Guard (`upload_guard.py`)**: All uploaded documents are validated by extension, byte size, and magic bytes before parsing:
     - Allowed extensions: `.pdf`, `.txt`, `.md`, `.csv`, `.docx`, `.xlsx`, `.pptx` for Knowledge Base; `.pdf`, `.txt`, `.md` for AI Catalog Builder.
     - Size limits: PDF max `20 MB` and max `100 pages` (encrypted PDFs, embedded files, and XFA forms rejected); Office `.docx`/`.xlsx`/`.pptx` max `10 MB` compressed, max `100 MB` uncompressed, max `2,000` zip entries, macros (`vbaProject.bin` / `macroEnabled`) rejected, XML parsed via `defusedxml`; CSV max `10 MB`; TXT/MD max `2 MB` (binary signatures and NUL bytes rejected); multipart request max `50 MB` and max `5 files` per upload.

---

## 8. Data Protection, Retention Schedule, Sub-Processors, and Transfers

1. **Data Protection Roles**:
   - See [Annex C (EN)](./annexes/annex-c-data-processing-and-retention.en.md) / [Lampiran C (ID)](./annexes/annex-c-data-processing-and-retention.id.md).
   - **Customer as Data Controller / Platform as Data Processor**: For all Customer Content (product catalogs, prices, business documents, brand assets, custom instructions) and End-User / Shopper personal data (chat messages, contact snippets shared in chat, uploaded product search photos, Virtual Try-On user/room photos, WhatsApp phone numbers, Telegram user/chat IDs) processed by the Customer's AI Agents.
   - **Platform as Independent Data Controller**: For Customer account registration data (`email`, `phone_number`, `full_name`, `business_name`, `username`, `password` hash), authentication/device tokens, subscription/invoice/wallet records, usage metering logs, administrative audit logs, and aggregated platform analytics.
2. **Verified Data Retention Schedule**:
   - **Registration OTP & Session**: 5 minutes (`300s`) for OTP; 15 minutes (`900s`) for uncompleted registration session.
   - **Authentication Tokens**: 15 minutes (`900s`) for JWT access token; 7 days (`604800s`) for refresh token; 30 days for remembered login device token; 15 minutes for failed-login rate-limit counters.
   - **Deployment Log Stream**: 2 hours in Redis (`deploy:log:<serviceID>`).
   - **End-User Chat History & Session State**: 24 hours (`CONVERSATION_TTL_SECONDS = 86400`) from last activity across LangGraph checkpoints, WebApp session state, pinned visitor contact details (up to 3 lines, 300 chars each), and browser IndexedDB cache; 10 minutes (`600s`) for undelivered WebSocket reply frames.
   - **Uploaded Media (Catalog Images, VTO Reference Images, Chat/VTO Uploads)**: Stored in cloud object storage (`Cloudflare R2`) and/or agent database while the AI Agent is active; per-agent database is dropped 15 days after suspension or immediately upon manual AI Agent deletion.
   - **Visitor Analytics (`tracker`)**: 90 days (`RetentionDays = 90`) for raw session reports (`tracker_session_reports`), per-visitor daily records, and daily rollups (`tracker_daily`). Raw session reports and per-visitor records are deleted immediately upon manual AI Agent deletion or post-retention purge; daily aggregated rollups expire automatically via 90-day TTL. Raw browser `User-Agent` strings are never sent to the central tracker (only coarse `device.type`, `device.os`, `device.browser`); visitors are keyed by a one-way SHA-256 hash (`visitor_hash`).
   - **Suspended AI Agent Data**: 15 days (`BillingSuspendRetentionDays = 15`) after service suspension before automated permanent deletion.
   - **Admin Account Action Audit Snapshots**: Personal fields (`email`, `phone_number`, `full_name`, `business_name`) in `systemlog` account-action snapshots are retained in clear for **365 days** (`SnapshotRetention = 365 * 24h`) and then irreversibly masked (`a***@domain.com`, `***1234`, initials `B. S.`), while non-personal audit identifiers (`user_id`, `username`, `roles`, action, reason, timestamp) remain for audit integrity.
   - **Billing, Invoice, and Wallet Ledger Records**: Retained as permanent financial and audit records (not deleted upon subscription termination); statutory tax/accounting retention period governed by applicable law (`[FINANCIAL RECORD RETENTION YEARS]`).
3. **Sub-Processors and Third-Party Dependencies (Internal Mapping -> Customer-Facing Category)**:
   - **Cloud Compute, Database & Cache Hosting** (Internal: Railway, MongoDB, Redis, Qdrant) -> Described in Terms as: *Cloud infrastructure, application hosting, and managed database/vector-search providers*.
   - **Network Edge, DNS, Bot Protection & Object Storage** (Internal: Cloudflare DNS/WAF, Cloudflare Turnstile, Cloudflare R2) -> Described in Terms as: *Content delivery, domain routing, security/bot-verification, and cloud object storage providers*.
   - **AI, LLM, Vision & Image Generation Providers** (Internal: OpenAI, Google Gemini, Anthropic, OpenRouter, NVIDIA, MiniMax, Ollama) -> Described in Terms as: *Third-party artificial intelligence, natural language processing, computer vision, and image generation model providers*.
   - **Payment Gateway** (Internal: Midtrans) -> Described in Terms as: *Licensed third-party payment gateway and payment processing providers*.
   - **Transactional Email Delivery** (Internal: Hostinger Email API) -> Described in Terms as: *Transactional email delivery providers*.
   - **Identity & Single Sign-On** (Internal: Google Identity Services) -> Described in Terms as: *Third-party identity and single sign-on authentication providers*.
   - **Customer Messaging Channels** (External Customer-connected: WhatsApp Business / Meta, Telegram) -> Named directly in Terms as *WhatsApp* and *Telegram*.
4. **Cross-Border Data Transfers**:
   - Because cloud hosting, object storage, and third-party AI model providers operate globally, Customer Content and End-User inputs/images may be transmitted to and processed in jurisdictions outside the Republic of Indonesia.
5. **Certifications and Compliance Posture**:
   - The codebase implements technical safeguards (encryption of master passwords when configured, bcrypt password hashing, JWT revocation denylists, rate limiting, CSRF protection, SHA-512 webhook verification, upload validation, AI guardrails), and a code comment references `SOC 2 CC6.1` as a design principle for AES-256-GCM encryption.
   - **Crucial Constraint**: The platform **does not** hold ISO/IEC 27001, SOC 2 Type I/II, PCI-DSS, or HIPAA certification. The Terms must never claim any such certification.

---

## 9. Current State of Terms Acceptance in the Codebase

1. **Frontend (`templates/register.html` & `assets/js/register.js`)**:
   - Step 3 of the registration form renders an `<input type="checkbox" id="terms" name="terms" required>` with links to Terms & Conditions and Privacy Policy (`href="#"`).
   - `assets/js/register.js` checks `termsCheckbox.checked` client-side before enabling/submitting Step 3 (`POST /api/v1/register/complete`).
2. **Backend (`internal/interface/api/v1/handler/register.go` & `internal/usecase/register/complete.go`)**:
   - `CompleteRegistrationRequest` currently binds only `session_id`, `business_name`, `full_name`, `username`, and `password`.
   - Neither `POST /api/v1/register/complete` nor `POST /api/v1/login/google` currently persists a Terms acceptance record (accepted version, timestamp, account identifier, or acceptance method), nor is there a middleware/gate requiring re-acceptance when the Terms version increments.
   - [acceptance-implementation.md](./acceptance-implementation.md) specifies the exact backend, database, and frontend implementation required to close this evidentiary gap.
