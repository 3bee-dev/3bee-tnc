# 21. Annex A. Subscription Plans, Quotas, AI Models, and Credit System Schedule

- Document Path: [annexes/annex-a-subscription-plans-quotas-credits.en.md](./annex-a-subscription-plans-quotas-credits.en.md)
- Counterpart Language Document Path: [annexes/annex-a-subscription-plans-quotas-credits.id.md](./annex-a-subscription-plans-quotas-credits.id.md)
- Parent Agreement Document Path: [terms-and-conditions.en.md](../terms-and-conditions.en.md#21-annex-a-subscription-plans-quotas-ai-models-and-credit-system-schedule)
- Table of Contents Document Path: [TOC.en.md](../TOC.en.md#21-annex-a-subscription-plans-quotas-ai-models-and-credit-system-schedule)

### 21.1. Subscription Plan Parameters and Frozen Period Snapshots

21.1.1. Each Subscription Plan in the Platform catalog specifies the following operational parameters:
(a) Maximum Active AI Agents: The maximum number of AI Agents that may be deployed and running concurrently.
(b) Monthly Package Quota for Chat Responses: The Stage 1 periodic unit allowance for AI chat responses.
(c) Monthly Package Quota for Virtual Try-On: The Stage 1 periodic unit allowance for Virtual Try-On image generations.
(d) Monthly Credit Pool: The Stage 2 periodic allowance of AI Credits included with the plan.
(e) Knowledge Base Document Limit: The maximum number of documents that may be stored across the Customer's AI Agents.
(f) Eligible AI Models: The list of AI Models selectable by the Customer and each model's assigned Quota Multiplier.
(g) Channel Entitlements: Whether WhatsApp Business integration and Telegram bot integration are enabled for the plan.

21.1.2. All parameters listed in Section 21.1.1, together with the Customer's settled subscription price and Billing Cycle (monthly or annual), are captured into a frozen Quota Snapshot at the start of each Billing Cycle in accordance with [Article 5 of the Agreement (terms-and-conditions.en.md)](../terms-and-conditions.en.md#5-article-5-subscription-plans-quotas-ai-models-and-credit-system).

### 21.2. AI Model Multipliers, Default Credit Tariffs, and Consumption Rules

21.2.1. When an AI Agent processes a metered chat response or Virtual Try-On generation:
(a) In Stage 1 (Monthly Package Quota), the Platform deducts one unit multiplied by the applicable Quota Multiplier from the corresponding quota counter, where the Quota Multiplier is an integer of one (1) or greater configured for the active AI Model.
(b) In Stage 2 (Monthly Credit Pool) and Stage 3 (Credit Balance), the Platform deducts the per-action Credit tariff configured for the selected AI Model and action type.
(c) Unless a specific AI Model displays a custom per-action Credit tariff in the Main Dashboard, the default Credit tariffs are two hundred fifty (250) Credits per chat response and two thousand (2,000) Credits per Virtual Try-On generation.
(d) Per-action Credit tariffs configured by the Provider on the Platform shall not exceed one million (1,000,000) Credits per single action.

### 21.3. Credit Balance Top-Up Boundaries and Ledger Rules

21.3.1. Credit Balance top-up purchases are subject to the following boundaries:
(a) Conversion Value: One (1) Credit equals one (1) Indonesian Rupiah (1 Credit = 1 IDR).
(b) Minimum Top-Up Amount: Ten thousand (10,000) Credits (IDR 10,000) per transaction.
(c) Maximum Top-Up Amount: One hundred million (100,000,000) Credits (IDR 100,000,000) per transaction.
(d) Maximum Pending Top-Up Invoices: Three (3) concurrent unpaid top-up invoices per Customer account.
(e) Expiration: Settled Credit Balance top-ups do not expire at the end of a Monthly or Annual Billing Cycle.
