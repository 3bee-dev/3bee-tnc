# 22. Annex B. Acceptable Use Policy and Document Upload Specifications

- Document Path: [annexes/annex-b-acceptable-use-and-uploads.en.md](./annex-b-acceptable-use-and-uploads.en.md)
- Counterpart Language Document Path: [annexes/annex-b-acceptable-use-and-uploads.id.md](./annex-b-acceptable-use-and-uploads.id.md)
- Parent Agreement Document Path: [terms-and-conditions.en.md](../terms-and-conditions.en.md#22-annex-b-acceptable-use-policy-and-document-upload-specifications)
- Table of Contents Document Path: [TOC.en.md](../TOC.en.md#22-annex-b-acceptable-use-policy-and-document-upload-specifications)

### 22.1. Prohibited Content and Unlawful Use Categories

22.1.1. Pursuant to [Article 8 of the Agreement (terms-and-conditions.en.md)](../terms-and-conditions.en.md#8-article-8-customer-obligations-acceptable-use-and-prohibited-conduct), the Customer shall not use any AI Agent, Hosted Web Storefront, Web Widget, WhatsApp connection, or Telegram connection to advertise, distribute, or process content relating to:
(a) Illegal narcotics, psychotropic substances, precursor chemicals, or unapproved pharmaceuticals.
(b) Online gambling, sports betting, lotteries, or unlicensed games of chance.
(c) Pornography, sexually explicit services, non-consensual intimate imagery, or any form of child sexual exploitation or abuse.
(d) Weapons, ammunition, explosives, or hazardous materials restricted by law.
(e) Stolen goods, counterfeit branded merchandise, pirated software, or unauthorized replicas.
(f) Ponzi schemes, pyramid schemes, unlicensed investment solicitation, money laundering, or payment fraud.
(g) Malicious hacking tools, credential harvesting, phishing pages, or deceptive impersonation of third-party brands or public authorities.

### 22.2. Document Upload File Types, Size Limits, and Structural Restrictions

22.2.1. Files uploaded by the Customer or its Operator Accounts are validated by file extension, byte length, file signature, and internal structure prior to ingestion:
(a) Supported Knowledge Base File Types: PDF, TXT, MD, CSV, DOCX, XLSX, and PPTX documents.
(b) Supported AI Catalog Extractor File Types: PDF, TXT, and MD documents.
(c) Portable Document Format (PDF) Limits: Maximum file size of twenty megabytes (20 MB) and maximum length of one hundred (100) pages. Encrypted or password-protected PDF files, PDF files containing embedded file attachments, and PDF files using dynamic XML form architectures are rejected.
(d) Office Document (DOCX, XLSX, PPTX) Limits: Maximum compressed file size of ten megabytes (10 MB), maximum uncompressed archive size of one hundred megabytes (100 MB), and maximum of two thousand (2,000) internal archive entries. Office documents containing embedded macros or unsafe external XML entities are rejected.
(e) Comma-Separated Values (CSV) Limits: Maximum file size of ten megabytes (10 MB), validated as genuine text content.
(f) Plain Text and Markdown (TXT, MD) Limits: Maximum file size of two megabytes (2 MB). Files containing binary executable signatures or null bytes are rejected.
(g) Batch Upload Limits: Maximum of five (5) files and maximum combined payload size of fifty megabytes (50 MB) per upload request.

### 22.3. AI Safety Guardrails, Vision Filters, and Visitor Session Rate Limits

22.3.1. The Platform enforces the following automated runtime controls on all deployed AI Agents:
(a) Prompt-Injection Guardrail: Incoming chat messages are screened by a two-tier pattern detector and an independent safety classification model to block instructions attempting to override system rules or extract internal prompts.
(b) Out-of-Scope Programming Filter: Requests asking a commercial shopping or receptionist AI Agent to write, debug, or execute software code are declined or redirected to store assistance.
(c) Virtual Try-On Vision Guardrail: Photos submitted for Virtual Try-On are evaluated by an independent vision suitability classifier prior to image generation, and requests are rate-limited to one request per thirty (30) seconds per sender with a three-hundred (300) second generation timeout.
(d) Configurable Visitor Session Rate Limits: The Customer may configure per-visitor-session request limits in the Main Dashboard between one (1) and ten thousand (10,000) requests per one (1) to four (4) minute window for chat responses and Virtual Try-On generations, or set them to unlimited.
