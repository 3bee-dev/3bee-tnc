# 23. Annex C. Data Processing and Retention Schedule

- Document Path: [annexes/annex-c-data-processing-and-retention.en.md](./annex-c-data-processing-and-retention.en.md)
- Counterpart Language Document Path: [annexes/annex-c-data-processing-and-retention.id.md](./annex-c-data-processing-and-retention.id.md)
- Parent Agreement Document Path: [terms-and-conditions.en.md](../terms-and-conditions.en.md#23-annex-c-data-processing-and-retention-schedule)
- Table of Contents Document Path: [TOC.en.md](../TOC.en.md#23-annex-c-data-processing-and-retention-schedule)

### 23.1. Categories of Data Subjects, Personal Data, and Processing Roles

23.1.1. Data Processed as Data Processor (Customer as Data Controller pursuant to [Article 12 of terms-and-conditions.en.md](../terms-and-conditions.en.md#12-article-12-data-roles-processing-purposes-retention-sub-processors-cross-border-transfers-and-incident-handling)):
(a) Data Subjects: End Users (shoppers, website visitors, WhatsApp users, Telegram users) and individuals mentioned in Customer Content.
(b) Categories of Personal Data: Conversational messages, contact snippets voluntarily provided in chat (name, phone number, address, or email up to three pinned lines of three hundred characters each), product search photos, Virtual Try-On user photos and room photos, WhatsApp telephone numbers and profile names, Telegram user identifiers and chat identifiers, and one-way cryptographic visitor hashes.
(c) Processing Operations: Receiving, temporarily caching in session memory, evaluating against safety guardrails, passing to AI Models for response or image synthesis, delivering responses across the connected channel, and recording de-identified Visitor Analytics.

23.1.2. Data Processed as Independent Data Controller (Provider as Data Controller):
(a) Data Subjects: Customer account holders, representatives, and Operator Account users.
(b) Categories of Personal Data: Email address, telephone number, full name, business name, username, encrypted or hashed credentials, client network addresses, device tokens, subscription and invoice records, Credit Balance ledger entries, and administrative audit logs.
(c) Processing Operations: Account registration, identity verification, authentication, billing, payment reconciliation, quota metering, security enforcement, customer support, and legal compliance.

### 23.2. Schedule of Data Retention Periods and Automated Purge Rules

23.2.1. The Platform applies the following specific retention periods:
(a) Registration One-Time Password: Five (5) minutes (300 seconds).
(b) Uncompleted Registration Session: Fifteen (15) minutes (900 seconds).
(c) Main Dashboard Access Token: Fifteen (15) minutes (900 seconds).
(d) Main Dashboard Refresh Token: Seven (7) calendar days (604,800 seconds), or until earlier logout or password change.
(e) Trusted Login Device Token: Thirty (30) calendar days.
(f) Failed-Login Rate-Limit Counter: Fifteen (15) minutes.
(g) Real-Time Deployment Log Stream: Two (2) hours.
(h) End-User Chat History, Workflow Checkpoints, Web Session State, and Pinned Contact Snippets: Twenty-four (24) hours (86,400 seconds) from the last session interaction, plus up to twenty-four (24) hours in the End User's own browser local storage on the Hosted Web Storefront or Web Widget.
(i) Undelivered Real-Time Reply Buffer: Ten (10) minutes (600 seconds).
(j) Visitor Analytics (Raw Session Reports, Per-Visitor Daily Marks, and Daily Aggregated Rollups): Ninety (90) calendar days, or deleted earlier upon manual AI Agent deletion or post-suspension database purge.
(k) Suspended or Downgrade-Stopped AI Agent Dedicated Database: Fifteen (15) calendar days ([SUSPENSION RETENTION DAYS]) from the timestamp of Billing Suspension or per-agent stoppage, after which the dedicated per-agent database is permanently dropped.
(l) Administrative Account-Action Audit Snapshots: Personal Data fields (email address, telephone number, full name, and business name) are retained in clear text for three hundred sixty-five (365) calendar days and are then automatically and irreversibly masked (retaining only the first character and domain of the email address, the last four digits of the telephone number, and name initials), while non-personal audit metadata (account identifier, username, roles, action, reason, and timestamp) is retained permanently for audit integrity.
(m) Customer Account, Credit Balance Ledger, and Invoice/Payment Records: Retained while the Customer account exists and for [FINANCIAL RECORD RETENTION YEARS, e.g., ten (10) years] thereafter to satisfy statutory tax, accounting, and dispute-evidence obligations.

### 23.3. Authorised Sub-Processor Categories and Cross-Border Transfer Safeguards

23.3.1. The Provider utilizes Sub-Processors in the following functional categories:
(a) Cloud Infrastructure and Managed Database Providers: For application runtime containers, relational/document database storage, in-memory session caching, and vector similarity search indexing.
(b) Network Edge, Domain Routing, Bot Protection, and Object Storage Providers: For custom subdomain routing, web traffic security, automated bot-verification challenges, and cloud object storage of product images, brand logos, and Virtual Try-On media.
(c) Artificial Intelligence Model Providers: For large language model chat generation, safety classification, document optical character recognition and extraction, computer vision analysis, and Virtual Try-On image synthesis.
(d) Licensed Payment Gateway Providers: For processing Indonesian Rupiah subscription payments and Credit Balance top-ups.
(e) Transactional Email Providers: For delivering one-time passwords, security alerts, payment reminders, and billing notices.
(f) Identity Authentication Providers: For optional third-party single sign-on authentication.

23.3.2. Where Sub-Processors process Personal Data outside the Republic of Indonesia, the Provider selects reputable commercial providers subject to data security and confidentiality commitments and transmits only the data elements necessary for the specific processing task.
