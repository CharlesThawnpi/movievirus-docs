# MovieVirus Master Implementation Plan

# =========================================================
# SEC-01. HEADER
# =========================================================

## Header
- Project: MovieVirus
- Document Type: Master Implementation Plan
- Purpose: Single source of truth for future implementation planning, module-by-module build design, phase-by-phase rollout, and VS Code prompt generation
- Status: Active Planning Draft
- Owner: Charles

---

# =========================================================
# SEC-02. VERSION BLOCK
# =========================================================

## Version Block
- Version: 1.1.0
- Last Updated: 2026-03-27
- Update Method: Section-based manual update
- Update Rule: Prefer updating only the affected phase, module, feature, dependency, risk, queue item, or prompt source instead of regenerating the whole document

---

# =========================================================
# SEC-03. CHANGE LOG
# =========================================================

## Change Log

### CHG-001 | 2026-03-27
- Initial Master Implementation Plan created
- Added planning rules, scope, business model, modules, phases, dependencies, risks, future additions queue, and prompt source sections
- Established stable IDs for future modular updates

### CHG-002 | 2026-03-27
- Added PostgreSQL as recommended target database
- Added legacy migration planning logic
- Added database normalization, entitlement carry-over, and media index reuse guidance
- Added migration-related phases, dependencies, risks, and prompt-source rules

### CHG-003 | 2026-03-27
- Added VPS naming abstraction guidance so personal labels are not treated as implementation identifiers
- Added WebApp-first control clarification so user and member management is backend/webapp controlled, not Telegram controlled
- Improved environment-neutral wording for future implementation prompts

### CHG-004 | 2026-03-27
- Reordered document sections into cleaner planning order
- Removed duplicate migration fragments by integrating them into standard module, phase, dependency, risk, queue, and prompt sections
- Preserved stable IDs while improving scanability and future update targeting

### CHG-005 | 2026-03-27
- Refined update protocol so future implementation-plan edits must reference exact existing headings or stable IDs
- Disallowed invented placement labels when the heading does not exist in the current document
- Improved paste-ready targeting format to support easier manual updates and safer VS Code prompt preparation

### CHG-006 | 2026-03-27
- Defined structured plan tiers with quota, daily cap, and sharing limits
- Introduced controlled sharing model via max linked accounts
- Added initial plan seed configuration
- Strengthened enforcement rules for linked accounts

### CHG-007 | 2026-03-27
- Expanded Module 10 from entity list into final Phase-1 PostgreSQL schema blueprint
- Added concrete table structure for plans, tokens, members, linked accounts, usage, payments, audit, and admin control
- Added atomic entitlement transaction dependency
- Added concurrency risk and mitigation for quota correctness

### CHG-08 | 2026-03-27
- Finalized token UX (single entry, no repeat for linked users)
- Introduced automatic oldest-account replacement policy
- Set token expiry to 90 days
- Added delivery retry logic (max 3 attempts)
- Defined duplicate request protection window (30–60 seconds)
- Simplified admin model for Phase 1

### CHG-09 | 2026-03-27
- Introduced full backend API layer design
- Defined endpoint groups and responsibilities
- Implemented indirect file delivery via secondary bot
- Added duplicate protection logic
- Added retry and failure handling rules
- Added API enforcement dependency
- Added redirect payload security risk

### CHG-10 | 2026-03-27
- Added Module 14 backend API contracts with JSON-level request/response structure
- Defined search, access validation, request validation, delivery verification, commit, payment, and admin endpoints
- Added signed delivery payload dependency for indirect multi-bot file delivery
- Added replay/tamper risk coverage for short-lived delivery payloads

### CHG-012 | 2026-03-27
- Added Node.js backend implementation blueprint
- Defined project structure and module responsibilities
- Defined transaction logic and middleware layer
- Added Phase 1 build order and constraints

### CHG-013 | 2026-03-27
- Added VPS-1 backup and data migration strategy
- Defined migration as transformation process, not direct restore
- Added mapping, validation, and rollback strategy
---

# =========================================================
# SEC-04. UPDATE PROTOCOL
# =========================================================

## Update Protocol
Use this document as the implementation planning source.

Future updates should follow these rules:
1. Do not rewrite the whole document unless explicitly requested.
2. Update only the relevant phase, module, feature, dependency, risk, queue item, or prompt source.
3. Preserve numbering and IDs where possible.
4. Add new features under the correct module using the format `Mxx-Fxx`.
5. Add new phases using the format `PH-xx`.
6. Add dependencies using the format `DEP-xx`.
7. Add risks using the format `RSK-xx`.
8. Add roadmap items into the Future Additions Queue before promoting them into active implementation sections.
9. Update the Change Log whenever a meaningful change is made.
10. Generate VS Code prompts from this document only after source planning sections are updated.
11. Prefer integrating updates into the correct standard section instead of appending detached add-on blocks.
12. When giving update instructions, always reference exact existing section names, headings, or stable IDs that already exist in the current document.
13. Do not use invented placement labels such as "Admin Section", "Infrastructure Section", or similar unless those exact headings already exist in the current document.
14. If adding new text between existing sections, specify the insertion point using the nearest real heading or ID, such as:
   - "insert below `### BL-08`"
   - "insert below `### M09-F04`"
   - "insert above `## Phases`"
15. If the exact insertion point cannot be confirmed from the current document text, say so honestly and provide the update as:
   - target section name
   - nearest confirmed heading/ID
   - paste-ready text
   Do not pretend an unverified heading exists.
---

# =========================================================
# SEC-05. PLANNING RULES
# =========================================================

## Planning Rules

### PR-01. Implementation Planning Principle
This document is for future implementation planning, not for storing GPT behavior rules. It defines what to build, in what order, with what logic, and under which technical and operational rules.

### PR-02. Source Separation Rule
- Master Instruction Source = GPT thinking and update behavior
- Master Implementation Plan = build blueprint and future implementation logic

### PR-03. Modularity Rule
Every major implementation area should be organized into modules, features, phases, dependencies, and risks.

### PR-04. Incremental Rule
Build should be planned phase by phase, not as one giant implementation.

### PR-05. Traceability Rule
Important technical, workflow, and business decisions should remain traceable through versioning, change logs, dependencies, and risk notes.

---

# =========================================================
# SEC-06. PRODUCT DEFINITION
# =========================================================

## Product Vision
MovieVirus is a token-based Telegram file request and delivery platform designed to support scalable subscription access, linked Telegram accounts, flexible recovery and transfer flows, payment review, reporting, auditability, multilingual user experience, and future feature expansion.

The system should be:
- scalable
- secure
- fair
- support-friendly
- traceable
- modular
- future-proof

## Scope

### In Scope
- token-based subscription plans
- linked Telegram account access
- quota enforcement
- daily cap enforcement
- expiry logic
- upgrade/downgrade rules
- account replacement/recovery
- Telegram Stars payment support
- local manual payment with OCR-assisted review
- admin review controls
- reporting and audit history
- multilingual content layer
- user self-service
- notifications and alerts
- future prompt generation for implementation
- legacy migration planning and cutover readiness
- WebApp-based member management and admin control

### Out of Scope for Initial Build
- advanced anti-abuse scoring
- full automatic OCR payment approval
- complex family plan billing logic
- heavy analytics dashboards
- advanced content recommendation engine
- hardware fingerprinting
- commercial-grade identity verification

---

# =========================================================
# SEC-07. CORE BUSINESS LOGIC
# =========================================================

## Core Business Logic

### BL-01. Core Model
- Token = subscription entitlement
- Telegram account = linked access session
- Database = enforcement, reporting, and audit layer

### BL-02. Plan Logic
Each plan should usually define:
- price
- total quota
- daily cap
- duration/expiry
- max linked Telegram accounts

### BL-03. Usage Logic
- one successful file delivery consumes one quota unit
- failed token validation should not consume quota
- file not found should not consume quota
- bot/send failure should not consume quota
- duplicate requests within a short safe window may avoid double deduction
- admin may manually restore quota when justified

### BL-04. Linked Account Logic
- if Telegram account is already linked, allow normal validation
- if not linked and free slot exists, auto-link
- if max linked accounts is reached, deny new linkage unless replacement/reset/admin policy allows it

### BL-05. Upgrade/Downgrade Logic
- upgrade = immediate with fair recalculation
- downgrade = next renewal cycle unless explicitly changed later

### BL-06. Payment Logic
- support Telegram Stars and local manual payment
- for local manual payment screenshots, OCR should assist review, not replace approval in phase 1

### BL-07. Management Authority Logic
- user and member management is controlled from the WebApp and backend
- Telegram is not the source of truth for plans, quota, linked accounts, or token lifecycle
- Telegram acts as request, validation, and delivery interface only

### BL-08. Infrastructure Naming Logic
- labels such as VPS-1 and VPS-2 are owner-friendly names only
- implementation must use environment-based or role-based identifiers instead of personal server nicknames

### BL-09. Legacy Migration Logic
For legacy transition:
- PostgreSQL is the recommended target database
- legacy SQLite data should be treated as source input, not as the target schema design
- active subscriptions must remain valid through their carried-over entitlement period
- valid media index data should be reused when delivery references remain operational
- expired or already used short-lived delivery tokens should not be migrated as active target tokens
- insecure legacy storage patterns must be removed during migration

---

# =========================================================
# SEC-08. MODULES
# =========================================================

## Modules

## Module 01. Subscription Plans and Token Entitlement

### M01-F01. Plan Definitions
Define:
- plan name/code
- price
- quota
- daily cap
- duration
- max linked accounts

### M01-F01-S01: Plan Configuration (Initial Seed Data)

System must allow dynamic plan creation via WebApp.

Initial seed plans:

Starter:
- price: 3000
- total_quota: 30
- daily_cap: 3
- max_linked_accounts: 1

Basic:
- price: 5000
- total_quota: 50
- daily_cap: 5
- max_linked_accounts: 2

Plus:
- price: 10000
- total_quota: 100
- daily_cap: 10
- max_linked_accounts: 3

Pro:
- price: 15000
- total_quota: 150
- daily_cap: 15
- max_linked_accounts: 4

Premium:
- price: 20000
- total_quota: 200
- daily_cap: 20
- max_linked_accounts: 5

Requirements:
- plans stored in database
- editable via admin panel
- no hardcoding in bot logic

### M01-F02. Token Statuses
Suggested statuses:
- Active
- Pending Activation
- Expired
- Suspended
- Revoked
- Exhausted

### M01-F03. Upgrade and Downgrade Policy
- upgrade = immediate
- downgrade = next renewal cycle

---

## Module 02. File Request and Quota Enforcement

### M02-F01. Search and Request Flow
- search file
- show found result
- request file
- ask token
- validate rules
- send file
- log usage
- deduct quota
Final Behavior Additions:

- token must be entered only once per Telegram account
- once linked, user is never asked for token again unless manually reset

Expiry:
- tokens expire after 90 days
- expiry must be enforced at validation stage

### M02-F02. Validation Rule
Check:
- token status
- expiry
- total quota remaining
- daily cap remaining
- linked-account eligibility

### M02-F03. Fair Use Protection
- no deduction on failed validation
- no deduction on file not found
- no deduction on send failure
- duplicate protection window

### M02-F04. Telegram Role Limitation
Telegram bot is not a membership system.
It acts as:
- request handler
- token validator through backend
- file delivery interface

It must not:
- manage plans as the source of truth
- manage upgrades/downgrades independently
- store quota as authoritative state

All critical decisions must be validated through backend APIs and database state.

---

## Module 03. Linked Accounts / Device Slots

### M03-F01. Linked Account Logic
- linked account reuse
- auto-link if slot available
- deny if no slot and no allowed replacement path
Delivery Retry Logic:

- system must retry failed file send up to 3 times
- if all retries fail:
   - mark request as send_failed
   - do not deduct quota
   - notify user
   - trigger admin notification

### M03-F02. Naming Rule
Use:
- Linked Accounts
- Allowed Accounts
- Device Slots

### M03-F03. Same Person Policy
Do not try to prove same-human identity. Enforce slot policy only.

---

## Module 04. Account Transfer, Replacement, and Recovery

### M04-F01. Add New Account
Allow when free slot exists.

### M04-F02. Replace Account
Allow according to plan or policy if slots are full.

### M04-F03. Lost Device Recovery
Support admin reset and optional limited self-reset later.

### M04-F04. Transfer Code Flow
Allow one-time short-lived transfer code from current linked account to a new account.

---

## Module 05. Security and Abuse Prevention

### M05-F01. Token Security
- long random tokens
- hashed storage
- masked previews

### M05-F02. Validation Protection
- rate limiting
- cooldown/lockout
- suspicious attempt logging

### M05-F03. Recovery Security
- log linked-account additions, resets, replacements
- support revoke/reissue
- optional PIN later

---

## Module 06. Reporting, History, and Audit

### M06-F01. Admin Reporting

Enforcement Update:
- max_linked_accounts must be strictly enforced
- IF limit reached:
   - deny new account linking
   - provide clear error message
- linking does NOT consume quota
  
Admin should be able to inspect:
- payment history
- request history
- file delivery history
- linked-account history
- account reset/replacement history
- plan change history
- quota adjustment history
- suspicious activity history
- admin action history

Linked Account Replacement Rule:

- when max_linked_accounts limit is reached:
   - system must automatically replace the oldest linked account
   - oldest determined by linked_at timestamp

- replacement must:
   - update link status of old account
   - create new link for incoming account
   - log event in token_account_change_logs

- user must be informed of replacement action

### M06-F02. User Self-History
User should be able to inspect:
- current plan
- remaining quota
- daily usage
- payment history
- request history
- linked accounts
- recent account changes
- token status
- expiry date

### M06-F03. Audit Principle
Do not silently overwrite critical data. Prefer dedicated log/history records.

### M06-F04. Migration Audit Extension
Migration-related reporting should preserve:
- old-to-new ID mapping
- migration run logs
- rejection logs
- cutover checkpoints
- parity verification evidence

---

## Module 07. Payments and Activation

### M07-F01. Payment Methods
- Telegram Stars
- local manual payment

### M07-F02. Manual Payment Flow
- choose plan
- show payment instructions
- upload screenshot
- OCR pre-check
- pending review
- approve/reject
- activate token after approval

### M07-F03. Backend API Layer (Core Design)

System must use a centralized backend API as the single source of truth.

All critical logic must be handled by backend:
- token validation
- quota enforcement
- daily cap checks
- linked account logic
- payment activation
- request logging
- duplicate protection

Clients:
- Telegram Bot (user-facing)
- WebApp (admin-facing)

Bot MUST NOT enforce business rules independently.


### M07-F04. Payment Statuses
- Pending
- OCR Matched
- OCR Uncertain
- Approved
- Rejected
- Refunded
- Expired Pending

#### 1. Auth / System
- POST /internal/auth/verify-service-key

#### 2. Token & Access
- POST /token/validate-and-link
- POST /token/validate-linked
- GET /token/status

#### 3. File Request Flow
- POST /request/validate
- POST /request/commit-success
- POST /request/commit-failure

#### 4. Search
- GET /search/files
- GET /search/details

#### 5. Payment
- POST /payment/submit
- POST /payment/approve
- POST /payment/reject

#### 6. Admin (WebApp)
- POST /admin/token/create
- POST /admin/token/update
- POST /admin/token/revoke
- POST /admin/token/adjust-quota
- GET /admin/token/logs
- GET /admin/payment/list

### M07-F05. Request Flow via API

1. User selects file

2. Bot calls:
POST /request/validate

Backend checks:
- token status
- expiry
- quota
- daily cap
- linked account

Response:
- approved / denied
- denial reason (if any)

3. IF approved:
Bot sends "Download via ..." link

4. User clicks link → redirected to delivery bot

5. Delivery bot sends file with:
- expiration timer (3 minutes)
- auto-delete after timeout

6. After successful send:
Bot calls:
POST /request/commit-success

7. If send fails after 3 retries:
Bot calls:
POST /request/commit-failure
→ backend logs
→ admin notified

### M07-F06. Secure File Delivery Design

File delivery must use indirect method to reduce Telegram bot ban risk.

Flow:
- primary bot does NOT send file directly
- primary bot sends:
   "Download via ..." button

Button contains:
- signed payload (token_id + request_id + expiry)

User is redirected to:
- secondary delivery bot

Delivery bot:
- validates payload via backend
- sends file
- enforces:
   - max 3-minute availability
   - auto-delete after timeout

Purpose:
- distribute risk across bots
- reduce ban probability
- maintain controlled access

### M07-F07. Duplicate Protection

Definition:
- duplicate request = same token + same telegram_user_id + same file within 30–60 seconds

Backend must:
- generate duplicate_guard_key
- reject duplicate with status:
   duplicate_ignored

Bot must:
- show user message explaining duplicate protection
- NOT deduct quota

### M07-F08. Linked Account Replacement via API

When new user links and limit is reached:

Backend must:
- identify oldest linked account (linked_at ASC)
- mark old account as replaced
- create new link

Response must include:
- replacement_flag = true
- replaced_account_info

Bot must:
- notify new user
- optionally notify removed user (if reachable)

### M07-F09. Retry & Failure Handling

Bot must:
- retry file send up to 3 times

If all fail:
- call /request/commit-failure

Backend must:
- log failure
- NOT deduct quota
- trigger admin notification

User must receive:
- clear status message

---

## Module 08. Multilingual Interface and Content Layer

### M08-F01. Language Strategy
Prefer Burmese-first UI with English toggle.

### M08-F02. Content Storage Rule
Store content by message key with Burmese and English variants.

---

## Module 09. Admin Controls

### M09-F01. Plan Management
- create/edit plans
- change price
- change quota
- change daily cap
- change linked account limit
- change duration

### M09-F02. Token Management
- generate token
- assign plan
- activate/deactivate token
- revoke token
- reissue token
- extend expiry
- add bonus quota

### M09-F03. Review and Recovery Controls
- inspect linked accounts
- inspect payment submissions
- approve/reject payments
- reset linked accounts
- perform manual overrides with logs

### M09-F04. WebApp Management Authority
The WebApp and backend admin system are the only authoritative places where user/member state is modified.

This includes:
- plan assignment
- quota adjustment
- token activation and revocation
- linked-account management
- payment review outcomes
- recovery and reset actions

Telegram should reflect backend state, not define it.

---

## Module 10. Database Design

### M10-F01. Core Entities
- plans
- tokens
- token_linked_accounts
- token_usage_logs
- daily_usage_counters

### M10-F02. Extended Entities
- token_transfer_requests
- token_account_change_logs
- payment_transactions
- payment_review_logs
- subscription_plan_change_logs
- admin_action_logs
- token_verification_attempt_logs
- user_language_preferences
- notification_logs

### M10-F03. Legacy Migration Database Rule
For migration, use PostgreSQL as the target database and do not reuse the legacy SQLite schema directly as the production target design.

### M10-F04. Migration Mapping Guidance
Recommended mapping:
- users -> members
- daily_usage -> member_daily_usage
- transactions -> payments
- delivery_tokens -> access_tokens plus access_token_items when batch payload normalization is required
- movies and series -> media_assets or retained split media tables depending on final schema decision
- series_episode_map -> media_episode_map
- request_events / search_miss / ai_events -> analytics tables

### M10-F05. Normalization Rule
Before import:
- recompute member status from dates instead of trusting legacy status blindly
- preserve original legacy IDs in mapping columns
- normalize CSV batch payloads into child rows
- clean orphan rows
- normalize enums and plan references
- enforce target-side foreign keys and indexes

### M10-F06. Final Phase-1 PostgreSQL Schema Blueprint

Use PostgreSQL as the production target database.

Schema design goals:
- backend/database as source of truth
- WebApp-driven member/admin management
- secure token handling
- controlled sharing via max linked accounts
- traceable quota, payment, and admin actions
- migration-safe and audit-friendly structure

Recommended table groups:
- plan and entitlement tables
- linked-account and quota enforcement tables
- payment and review tables
- audit and support tables
- optional content/localization tables

### M10-F07. Core Plan and Entitlement Tables

#### Table: plans
Purpose:
- stores admin-configurable subscription plans

Fields:
- id (uuid, pk)
- code (varchar, unique, not null)  
  Example: STARTER, BASIC, PLUS
- name (varchar, not null)
- description (text, nullable)
- price_mmk (integer, not null)
- price_stars (integer, nullable)
- total_quota (integer, not null)
- daily_cap (integer, not null)
- duration_days (integer, not null)
- max_linked_accounts (integer, not null)
- is_active (boolean, default true)
- sort_order (integer, default 0)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Constraints:
- total_quota > 0
- daily_cap > 0
- max_linked_accounts >= 1
- duration_days > 0

Indexes:
- unique(code)
- index(is_active, sort_order)

#### Table: tokens
Purpose:
- stores one subscription entitlement instance per token

Fields:
- id (uuid, pk)
- plan_id (uuid, fk -> plans.id, not null)
- token_hash (varchar, unique, not null)
- token_masked (varchar, not null)
- status (varchar, not null)
- activated_at (timestamptz, nullable)
- expires_at (timestamptz, nullable)
- total_quota_initial (integer, not null)
- total_quota_remaining (integer, not null)
- daily_cap_snapshot (integer, not null)
- max_linked_accounts_snapshot (integer, not null)
- price_mmk_snapshot (integer, not null)
- price_stars_snapshot (integer, nullable)
- source_payment_transaction_id (uuid, nullable, fk -> payment_transactions.id)
- notes (text, nullable)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Status values:
- pending_activation
- active
- expired
- suspended
- revoked
- exhausted

Rules:
- store hash only, never plaintext token
- snapshots preserve historical truth even if plan changes later
- token becomes exhausted when total_quota_remaining <= 0

Indexes:
- unique(token_hash)
- index(plan_id)
- index(status)
- index(expires_at)

#### Table: members
Purpose:
- optional purchaser/member profile managed from WebApp
- separates customer/support identity from Telegram account rows

Fields:
- id (uuid, pk)
- display_name (varchar, nullable)
- phone_number (varchar, nullable)
- email (varchar, nullable)
- default_language (varchar, default 'my')
- status (varchar, not null, default 'active')
- notes (text, nullable)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Status values:
- active
- suspended
- archived

Indexes:
- index(status)
- index(phone_number)
- index(email)

#### Table: member_tokens
Purpose:
- links purchaser/member profile to owned token(s) for WebApp support visibility
- does not replace token-linked-account enforcement

Fields:
- id (uuid, pk)
- member_id (uuid, fk -> members.id, not null)
- token_id (uuid, fk -> tokens.id, not null)
- relationship_type (varchar, not null, default 'owner')
- is_primary (boolean, default true)
- linked_at (timestamptz, not null)
- created_at (timestamptz, not null)

Relationship types:
- owner
- assigned_by_admin
- migrated_legacy_owner

Indexes:
- unique(member_id, token_id)
- index(token_id)

### M10-F08. Telegram Account and Quota Enforcement Tables

#### Table: token_linked_accounts
Purpose:
- enforces controlled sharing by Telegram account slots

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- telegram_user_id (bigint, not null)
- telegram_username (varchar, nullable)
- telegram_first_name (varchar, nullable)
- telegram_last_name (varchar, nullable)
- link_status (varchar, not null, default 'active')
- linked_at (timestamptz, not null)
- last_used_at (timestamptz, nullable)
- linked_by (varchar, not null, default 'auto')
- replaced_at (timestamptz, nullable)
- replacement_reason (text, nullable)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Link status values:
- active
- replaced
- removed
- blocked

Rules:
- one telegram_user_id may appear only once per token while active
- active linked account count must not exceed token.max_linked_accounts_snapshot

Indexes:
- unique(token_id, telegram_user_id)
- index(telegram_user_id)
- index(token_id, link_status)

#### Table: daily_usage_counters
Purpose:
- fast enforcement of per-token daily cap

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- usage_date (date, not null)
- successful_requests_count (integer, not null, default 0)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Rules:
- one row per token per day
- reset is natural by new date row, not by destructive overwrite

Indexes:
- unique(token_id, usage_date)

#### Table: token_usage_logs
Purpose:
- immutable request and delivery history

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- telegram_user_id (bigint, not null)
- linked_account_id (uuid, nullable, fk -> token_linked_accounts.id)
- request_key (varchar, not null)
- media_ref_type (varchar, nullable)
- media_ref_id (varchar, nullable)
- source_chat_id (bigint, nullable)
- source_message_id (bigint, nullable)
- delivery_chat_id (bigint, nullable)
- delivery_message_id (bigint, nullable)
- request_status (varchar, not null)
- quota_delta (integer, not null, default 0)
- duplicate_guard_key (varchar, nullable)
- failure_reason_code (varchar, nullable)
- requested_at (timestamptz, not null)
- delivered_at (timestamptz, nullable)
- created_at (timestamptz, not null)

Request status values:
- requested
- delivered
- duplicate_ignored
- validation_failed
- file_not_found
- send_failed
- quota_restored

Rules:
- deduct quota only when request_status = delivered
- failed validation, file not found, and send failure must use quota_delta = 0
- duplicate protection should rely on duplicate_guard_key or equivalent safe window logic

Indexes:
- index(token_id, requested_at desc)
- index(telegram_user_id, requested_at desc)
- unique(duplicate_guard_key) where duplicate_guard_key is not null

#### Table: token_verification_attempt_logs
Purpose:
- stores token verification attempts for security and support

Fields:
- id (uuid, pk)
- supplied_token_hash (varchar, nullable)
- matched_token_id (uuid, nullable, fk -> tokens.id)
- telegram_user_id (bigint, nullable)
- attempt_status (varchar, not null)
- failure_reason_code (varchar, nullable)
- source_context (varchar, not null, default 'telegram_bot')
- attempted_at (timestamptz, not null)
- ip_address (inet, nullable)
- user_agent (text, nullable)
- created_at (timestamptz, not null)

Attempt status values:
- success
- invalid_token
- expired
- suspended
- revoked
- exhausted
- linked_account_limit_reached
- cooldown_blocked

Indexes:
- index(matched_token_id, attempted_at desc)
- index(telegram_user_id, attempted_at desc)
- index(attempt_status, attempted_at desc)

Additional Rule:

- replacement logic must select oldest active linked account (linked_at ASC)
- update replaced account:
   - link_status = replaced
   - replaced_at = now()

### M10-F09. Payment, Review, and Plan Change Tables

#### Table: payment_transactions
Purpose:
- stores Telegram Stars and local manual payments

Fields:
- id (uuid, pk)
- member_id (uuid, nullable, fk -> members.id)
- plan_id (uuid, nullable, fk -> plans.id)
- payment_method (varchar, not null)
- payment_status (varchar, not null)
- amount_mmk (integer, nullable)
- amount_stars (integer, nullable)
- payer_reference (varchar, nullable)
- external_reference (varchar, nullable)
- screenshot_file_id (varchar, nullable)
- submitted_at (timestamptz, nullable)
- approved_at (timestamptz, nullable)
- rejected_at (timestamptz, nullable)
- approved_token_id (uuid, nullable, fk -> tokens.id)
- rejection_reason (text, nullable)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Payment methods:
- telegram_stars
- local_manual

Payment statuses:
- pending
- ocr_matched
- ocr_uncertain
- approved
- rejected
- refunded
- expired_pending

Indexes:
- index(member_id)
- index(plan_id)
- index(payment_status)
- index(payment_method)
- index(created_at desc)

#### Table: payment_review_logs
Purpose:
- immutable history of OCR and admin review actions

Fields:
- id (uuid, pk)
- payment_transaction_id (uuid, fk -> payment_transactions.id, not null)
- review_actor_type (varchar, not null)
- review_actor_id (uuid, nullable)
- review_step (varchar, not null)
- review_outcome (varchar, not null)
- review_notes (text, nullable)
- ocr_summary_json (jsonb, nullable)
- reviewed_at (timestamptz, not null)
- created_at (timestamptz, not null)

Review actor types:
- system
- admin

Review steps:
- ocr_precheck
- manual_review
- final_decision

Indexes:
- index(payment_transaction_id, reviewed_at desc)

#### Table: subscription_plan_change_logs
Purpose:
- preserves upgrade/downgrade history and fairness adjustments

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- old_plan_id (uuid, nullable, fk -> plans.id)
- new_plan_id (uuid, nullable, fk -> plans.id)
- change_type (varchar, not null)
- effective_at (timestamptz, not null)
- requested_at (timestamptz, not null)
- requested_by_admin_id (uuid, nullable)
- quota_adjustment_delta (integer, nullable)
- expiry_adjustment_days (integer, nullable)
- notes (text, nullable)
- created_at (timestamptz, not null)

Change types:
- initial_assignment
- upgrade
- downgrade_scheduled
- renewal
- migration_carryover
- manual_correction

Indexes:
- index(token_id, effective_at desc)

### M10-F10. Recovery, Audit, and Admin Tables

#### Table: token_account_change_logs
Purpose:
- tracks account linking, replacement, removal, and resets

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- old_telegram_user_id (bigint, nullable)
- new_telegram_user_id (bigint, nullable)
- change_type (varchar, not null)
- reason_code (varchar, nullable)
- performed_by_type (varchar, not null)
- performed_by_admin_id (uuid, nullable)
- change_notes (text, nullable)
- created_at (timestamptz, not null)

Change types:
- auto_link
- manual_link
- replace
- remove
- admin_reset
- migration_import

Indexes:
- index(token_id, created_at desc)

#### Table: quota_adjustment_logs
Purpose:
- records manual restores, bonus quota, or corrections separately from usage

Fields:
- id (uuid, pk)
- token_id (uuid, fk -> tokens.id, not null)
- adjustment_type (varchar, not null)
- delta_quota (integer, not null)
- before_remaining_quota (integer, not null)
- after_remaining_quota (integer, not null)
- reason_code (varchar, nullable)
- notes (text, nullable)
- performed_by_admin_id (uuid, nullable)
- created_at (timestamptz, not null)

Adjustment types:
- restore
- bonus
- correction
- migration_baseline

Indexes:
- index(token_id, created_at desc)

#### Table: admin_users
Purpose:
- stores WebApp admin/operator identities

Phase 1 Simplification:

- system may operate with a single admin user
- role structure remains for future expansion but is not required initially

Fields:
- id (uuid, pk)
- username (varchar, unique, not null)
- display_name (varchar, not null)
- role_code (varchar, not null)
- status (varchar, not null, default 'active')
- password_hash (varchar, not null)
- last_login_at (timestamptz, nullable)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Role codes:
- super_admin
- finance_admin
- support_admin
- reviewer

Indexes:
- unique(username)
- index(role_code, status)

#### Table: admin_action_logs
Purpose:
- full audit trail for admin-side changes

Fields:
- id (uuid, pk)
- admin_user_id (uuid, nullable, fk -> admin_users.id)
- action_type (varchar, not null)
- target_entity_type (varchar, not null)
- target_entity_id (uuid, nullable)
- action_summary (text, not null)
- before_json (jsonb, nullable)
- after_json (jsonb, nullable)
- created_at (timestamptz, not null)

Indexes:
- index(admin_user_id, created_at desc)
- index(target_entity_type, target_entity_id)
- index(action_type, created_at desc)

### M10-F11. Optional Support Tables for Phase-1 Readiness

#### Table: user_language_preferences
Purpose:
- stores Burmese/English preference per Telegram account

Fields:
- id (uuid, pk)
- telegram_user_id (bigint, unique, not null)
- language_code (varchar, not null, default 'my')
- updated_at (timestamptz, not null)
- created_at (timestamptz, not null)

#### Table: notification_logs
Purpose:
- records important outbound notifications

Fields:
- id (uuid, pk)
- token_id (uuid, nullable, fk -> tokens.id)
- telegram_user_id (bigint, nullable)
- notification_type (varchar, not null)
- channel (varchar, not null, default 'telegram')
- delivery_status (varchar, not null)
- payload_summary (text, nullable)
- sent_at (timestamptz, nullable)
- created_at (timestamptz, not null)

### M10-F12. Relationship and Enforcement Rules

Relationship summary:
- one plan -> many tokens
- one member -> many owned tokens
- one token -> many linked Telegram accounts up to max_linked_accounts_snapshot
- one token -> many usage logs
- one token -> many daily usage rows
- one payment transaction -> zero or one approved token
- one token -> many plan change logs
- one token -> many quota adjustment logs
- one token -> many verification attempt logs

Required enforcement behavior:
1. On token validation:
   - check token status
   - check expires_at
   - check total_quota_remaining
   - check daily usage count for current date
   - check linked-account eligibility

2. On successful delivery:
   - insert token_usage_logs row with request_status = delivered
   - decrement tokens.total_quota_remaining by 1
   - upsert daily_usage_counters for current date
   - commit as one transaction

3. On failed delivery or failed validation:
   - log event where relevant
   - do not decrement quota

4. On linking new Telegram account:
   - count active rows in token_linked_accounts
   - compare against max_linked_accounts_snapshot
   - insert link only if slot is available

5. On plan change:
   - preserve historical logs
   - write subscription_plan_change_logs
   - do not rewrite historical usage or payment records

6. On quota restore or bonus:
   - update token remaining quota
   - write quota_adjustment_logs
   - never hide the original usage history

Recommended technical standards:
- use UUID primary keys for business entities
- use timestamptz everywhere
- prefer append-only logs for audit tables
- use jsonb only for review metadata or before/after audit snapshots
- prefer database constraints and indexes over Telegram-side assumptions

### M10-F06. Delivery Integrity Rule
Validate inherited Telegram delivery references before cutover. If delivery depends on source chat/message mapping, sample verification is mandatory before decommissioning the legacy VPS.

### M10-F07. Migration Audit Tables
Maintain migration-related tables such as:
- migration_runs
- migration_row_audit
- migration_rejections
- cutover_checkpoints

---

## Module 11. User Self-Service

### M11-F01. User Menu
- My Plan
- My Remaining Quota
- My Request History
- My Payment History
- My Linked Accounts
- Manage Linked Accounts
- Change Language
- Help / Payment Guide

### M11-F02. Linked Account Self-Service
- add new account
- replace account
- request reset
- see linked-account history

---

## Module 12. Notifications and Messaging

### M12-F01. User Notifications
- payment pending
- payment approved
- payment rejected
- token activated
- expiry warning
- daily cap reached
- quota exhausted
- new linked account added
- linked account replaced
- reset completed

### M12-F02. Admin Alerts
- suspicious payment submission
- repeated failed token attempts
- unusual account linking activity
- manual review backlog

---

## Module 13. Legacy Migration and Cutover

### M13-F01. Migration Objective
Safely migrate legacy data and active users into the new system without breaking entitlement continuity, delivery integrity, or auditability.

### M13-F02. Target Database Rule
Use PostgreSQL as the target database. Do not reuse the legacy SQLite schema directly as the production target design.

### M13-F03. Data Classification Rule
Classify legacy data before import:
- MUST migrate: active member entitlement data, payment history, daily usage baselines where relevant, movies, series, episode mapping, core media references
- SHOULD migrate: analytics and reminder history where useful
- DISCARD or REBUILD: expired/used short-lived delivery tokens, stale request placeholders, obsolete cleanup queues, invalid orphan rows

### M13-F04. Security Remediation Rule
The new system must remove insecure legacy practices such as:
- plaintext token storage
- publicly exposed dev admin services
- missing relational integrity
- weak audit preservation

### M13-F05. Cutover Rule
Migration should use:
- immutable backup
- staging cleanup
- validation import
- final delta sync
- cutover switch
- rollback-safe read-only window for legacy infrastructure

### M13-F06. Post-Cutover Verification Rule
Verify:
- entitlement parity
- payment visibility parity
- media delivery integrity
- linked-account enforcement
- quota and daily-cap correctness
- rollback readiness before final legacy shutdown

## Module 14. Backend API Contracts

### M14-F01. API Contract Principles

API style:
- JSON request/response format
- versioned path prefix: `/api/v1`
- HTTPS required
- backend is the single source of truth
- Telegram bot and WebApp are clients only

Core rules:
- bot must not enforce quota, expiry, linked-account, or payment state independently
- plaintext token may be submitted over HTTPS to backend for validation; backend hashes/compares internally
- all critical enforcement results must come from backend/database state
- successful delivery, quota deduction, and daily counter update must remain atomic
- indirect file delivery must use signed short-lived payloads validated by backend before delivery

Response envelope:
- `success` = boolean
- `code` = stable machine-readable status code
- `message` = short human-readable summary
- `data` = object or null
- `meta` = optional object

Error format:
```json
{
  "success": false,
  "code": "TOKEN_EXPIRED",
  "message": "Token expired. Please renew or purchase a new plan.",
  "data": null,
  "meta": {
    "request_id": "req_01H..."
  }
}

M14-F02. Internal Client Authentication

Internal clients:

primary Telegram bot
delivery bot
WebApp admin panel

Required headers:

X-Service-Key: <server-side secret>
X-Client-Type: primary_bot | delivery_bot | webapp
X-Request-Id: <unique id>

Rules:

service keys are server-side only
user-facing Telegram clients must never see service keys
admin login/session is separate from internal service authentication
backend should reject requests with missing or invalid service key

Example:

{
  "headers": {
    "X-Service-Key": "svc_live_xxxxx",
    "X-Client-Type": "primary_bot",
    "X-Request-Id": "req_01J..."
  }
}
M14-F03. Search API
GET /api/v1/search/files

Purpose:

search movies/series before entitlement check
allow discovery first, then require token/purchase at request stage

Query params:

q = required string
year = optional integer
subtitle = optional string
page = optional integer
limit = optional integer

Success example:

{
  "success": true,
  "code": "SEARCH_OK",
  "message": "Search results found.",
  "data": {
    "items": [
      {
        "media_ref_id": "mov_100245",
        "media_ref_type": "movie",
        "title": "Example Movie",
        "year": 2024,
        "subtitle": "English",
        "availability": "available"
      }
    ]
  },
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 1
  }
}
GET /api/v1/search/details/{media_ref_id}

Purpose:

fetch full details for one result before request

Success example:

{
  "success": true,
  "code": "MEDIA_DETAILS_OK",
  "message": "Media details loaded.",
  "data": {
    "media_ref_id": "mov_100245",
    "media_ref_type": "movie",
    "title": "Example Movie",
    "year": 2024,
    "subtitle_options": ["English", "Myanmar"],
    "is_requestable": true
  },
  "meta": null
}
M14-F04. Token Entry and Link API
POST /api/v1/access/validate-and-link

Purpose:

used when requesting user is not yet linked
validates token
links Telegram account
auto-replaces oldest linked account if plan limit is full

Request:

{
  "token_plaintext": "MV-8F3K2L9XQ7P1A6N",
  "telegram_user": {
    "telegram_user_id": 123456789,
    "username": "example_user",
    "first_name": "Example",
    "last_name": "User"
  },
  "context": {
    "source": "primary_bot",
    "language_code": "my"
  }
}

Success without replacement:

{
  "success": true,
  "code": "TOKEN_VALIDATED_AND_LINKED",
  "message": "Token verified successfully.",
  "data": {
    "token_id": "tok_01J...",
    "plan": {
      "code": "BASIC",
      "name": "Basic",
      "total_quota_remaining": 47,
      "daily_cap": 5,
      "daily_remaining": 5,
      "expires_at": "2026-06-25T00:00:00Z"
    },
    "linked": true,
    "replacement": {
      "performed": false,
      "replaced_telegram_user_id": null
    }
  },
  "meta": null
}

Success with oldest-account replacement:

{
  "success": true,
  "code": "TOKEN_VALIDATED_LINKED_OLDEST_REPLACED",
  "message": "Token verified. Oldest linked account was replaced.",
  "data": {
    "token_id": "tok_01J...",
    "plan": {
      "code": "PLUS",
      "name": "Plus",
      "total_quota_remaining": 92,
      "daily_cap": 10,
      "daily_remaining": 10,
      "expires_at": "2026-06-25T00:00:00Z"
    },
    "linked": true,
    "replacement": {
      "performed": true,
      "replaced_telegram_user_id": 987654321
    }
  },
  "meta": null
}

Common denial codes:

INVALID_TOKEN
TOKEN_EXPIRED
TOKEN_SUSPENDED
TOKEN_REVOKED
TOKEN_EXHAUSTED
TOKEN_DAILY_CAP_REACHED
TOKEN_COOLDOWN_BLOCKED
M14-F05. Linked Account Validation API
POST /api/v1/access/validate-linked

Purpose:

used for already-linked Telegram accounts
should not require token input again unless manually reset

Request:

{
  "telegram_user_id": 123456789,
  "media_ref_id": "mov_100245",
  "media_ref_type": "movie"
}

Success example:

{
  "success": true,
  "code": "LINKED_ACCESS_OK",
  "message": "Linked account validated.",
  "data": {
    "token_id": "tok_01J...",
    "plan_code": "BASIC",
    "total_quota_remaining": 47,
    "daily_remaining": 5,
    "expires_at": "2026-06-25T00:00:00Z"
  },
  "meta": null
}

Common denial codes:

LINK_NOT_FOUND
TOKEN_EXPIRED
TOKEN_SUSPENDED
TOKEN_REVOKED
TOKEN_EXHAUSTED
TOKEN_DAILY_CAP_REACHED
M14-F06. Request Pre-Validation API
POST /api/v1/requests/validate

Purpose:

validates whether a file request may proceed before delivery link is issued

Request:

{
  "telegram_user_id": 123456789,
  "media_ref_id": "mov_100245",
  "media_ref_type": "movie",
  "request_context": {
    "source_chat_id": -100111222333,
    "source_message_id": 4567
  }
}

Success example:

{
  "success": true,
  "code": "REQUEST_APPROVED",
  "message": "Request approved.",
  "data": {
    "request_id": "req_01J...",
    "token_id": "tok_01J...",
    "duplicate_guard_key": "dup_01J...",
    "total_quota_remaining": 47,
    "daily_remaining": 5,
    "delivery_payload": {
      "signed_token": "dlp_xxxxx",
      "expires_at": "2026-03-27T12:03:00Z"
    }
  },
  "meta": null
}

Duplicate example:

{
  "success": false,
  "code": "DUPLICATE_REQUEST_IGNORED",
  "message": "Same file was requested recently. Please wait a moment.",
  "data": {
    "duplicate_window_seconds": 45
  },
  "meta": null
}

Common denial codes:

LINK_NOT_FOUND
TOKEN_EXPIRED
TOKEN_EXHAUSTED
TOKEN_DAILY_CAP_REACHED
FILE_NOT_FOUND
REQUEST_NOT_ALLOWED
M14-F07. Delivery Payload Verification API
POST /api/v1/delivery/verify-payload

Purpose:

called by delivery bot before sending file
validates signed short-lived payload from primary bot

Request:

{
  "signed_token": "dlp_xxxxx",
  "telegram_user_id": 123456789
}

Success example:

{
  "success": true,
  "code": "DELIVERY_PAYLOAD_VALID",
  "message": "Delivery payload verified.",
  "data": {
    "request_id": "req_01J...",
    "token_id": "tok_01J...",
    "media_ref_id": "mov_100245",
    "media_ref_type": "movie",
    "delivery_window_seconds": 180,
    "delete_after_seconds": 180,
    "file_source": {
      "mode": "telegram_reference",
      "file_chat_id": -100444555666,
      "file_message_id": 778899
    }
  },
  "meta": null
}

Denial codes:

DELIVERY_PAYLOAD_INVALID
DELIVERY_PAYLOAD_EXPIRED
DELIVERY_PAYLOAD_ALREADY_USED
DELIVERY_PAYLOAD_USER_MISMATCH
M14-F08. Request Commit Success API
POST /api/v1/requests/commit-success

Purpose:

called only after delivery bot successfully sends the file
deducts quota and updates daily counter atomically

Request:

{
  "request_id": "req_01J...",
  "telegram_user_id": 123456789,
  "delivery_result": {
    "delivery_chat_id": 123456789,
    "delivery_message_id": 999001,
    "delivered_at": "2026-03-27T12:01:30Z"
  }
}

Success example:

{
  "success": true,
  "code": "REQUEST_COMMITTED",
  "message": "Quota deducted successfully.",
  "data": {
    "token_id": "tok_01J...",
    "quota_delta": 1,
    "total_quota_remaining": 46,
    "daily_remaining": 4
  },
  "meta": null
}

Denial codes:

REQUEST_NOT_FOUND
REQUEST_ALREADY_COMMITTED
COMMIT_CONFLICT
M14-F09. Request Commit Failure API
POST /api/v1/requests/commit-failure

Purpose:

called when delivery fails after up to 3 retries
must not deduct quota
should trigger admin notification workflow

Request:

{
  "request_id": "req_01J...",
  "telegram_user_id": 123456789,
  "failure": {
    "reason_code": "SEND_FAILED_AFTER_RETRIES",
    "retry_count": 3,
    "last_error": "Telegram timeout"
  }
}

Success example:

{
  "success": true,
  "code": "REQUEST_FAILURE_RECORDED",
  "message": "Failure recorded. Quota not deducted.",
  "data": {
    "admin_notification_queued": true,
    "quota_delta": 0
  },
  "meta": null
}
M14-F10. Telegram Stars Payment API
POST /api/v1/payments/telegram-stars/webhook

Purpose:

receive confirmed Stars payment result
auto-approve and generate token immediately

Request:

{
  "telegram_charge_id": "tg_01J...",
  "plan_code": "BASIC",
  "telegram_user_id": 123456789,
  "amount_stars": 500,
  "currency": "XTR"
}

Success example:

{
  "success": true,
  "code": "PAYMENT_APPROVED_TOKEN_CREATED",
  "message": "Payment approved and token created.",
  "data": {
    "payment_transaction_id": "pay_01J...",
    "token_id": "tok_01J...",
    "token_masked": "MV-****-****-1A6N",
    "plan_code": "BASIC",
    "expires_at": "2026-06-25T00:00:00Z"
  },
  "meta": null
}
M14-F11. Manual Payment API
POST /api/v1/payments/manual/submit

Purpose:

submit local manual payment proof for admin review

Request:

{
  "plan_code": "PLUS",
  "member": {
    "display_name": "Example Buyer",
    "phone_number": "09xxxxxxx"
  },
  "payment": {
    "amount_mmk": 10000,
    "payer_reference": "KBZ-123456",
    "screenshot_file_id": "AgACAgUAAx..."
  }
}

Success example:

{
  "success": true,
  "code": "PAYMENT_SUBMITTED",
  "message": "Payment submitted for review.",
  "data": {
    "payment_transaction_id": "pay_01J...",
    "payment_status": "pending"
  },
  "meta": null
}
POST /api/v1/admin/payments/{payment_transaction_id}/approve

Purpose:

admin approval for local manual payment
generates token and returns/send-ready token details

Success example:

{
  "success": true,
  "code": "PAYMENT_APPROVED_TOKEN_CREATED",
  "message": "Payment approved and token created.",
  "data": {
    "payment_transaction_id": "pay_01J...",
    "token_id": "tok_01J...",
    "token_masked": "MV-****-****-1A6N",
    "plan_code": "PLUS",
    "expires_at": "2026-06-25T00:00:00Z",
    "delivery_action": "send_token_to_user"
  },
  "meta": null
}
POST /api/v1/admin/payments/{payment_transaction_id}/reject

Purpose:

reject local manual payment with reason

Request:

{
  "reason": "Screenshot does not match payment amount."
}
M14-F12. Admin Plan and Token APIs
GET /api/v1/admin/plans
POST /api/v1/admin/plans
PATCH /api/v1/admin/plans/{plan_id}

Plan response example:

{
  "success": true,
  "code": "PLAN_SAVED",
  "message": "Plan updated successfully.",
  "data": {
    "plan_id": "pln_01J...",
    "code": "PREMIUM",
    "price_mmk": 20000,
    "price_stars": 2000,
    "total_quota": 200,
    "daily_cap": 20,
    "duration_days": 90,
    "max_linked_accounts": 5,
    "is_active": true
  },
  "meta": null
}
POST /api/v1/admin/tokens/create
PATCH /api/v1/admin/tokens/{token_id}
POST /api/v1/admin/tokens/{token_id}/revoke
POST /api/v1/admin/tokens/{token_id}/extend-expiry
POST /api/v1/admin/tokens/{token_id}/adjust-quota
POST /api/v1/admin/tokens/{token_id}/reset-linked-accounts
GET /api/v1/admin/tokens/{token_id}/logs

Quota adjustment example:

{
  "delta_quota": 5,
  "reason_code": "manual_restore",
  "notes": "Delivery failure recovery"
}
M14-F13. Notifications and Status Message Contract

User-facing status codes that bot/UI should map clearly:

INVALID_TOKEN
TOKEN_EXPIRED
TOKEN_SUSPENDED
TOKEN_REVOKED
TOKEN_EXHAUSTED
TOKEN_DAILY_CAP_REACHED
DUPLICATE_REQUEST_IGNORED
TOKEN_VALIDATED_LINKED_OLDEST_REPLACED
REQUEST_APPROVED
REQUEST_COMMITTED
REQUEST_FAILURE_RECORDED
PAYMENT_SUBMITTED
PAYMENT_APPROVED_TOKEN_CREATED
PAYMENT_REJECTED

Rules:

all denial reasons must be user-readable
replacement events should notify both the incoming requester and replaced account when reachable
send-failure events should notify requester and admin
delivery link expiry/delete timing should be made visible to user
M14-F14. API Idempotency and Logging Rules

Rules:

all mutating endpoints should accept or generate a request correlation ID
commit endpoints must be idempotent to prevent double deduction
duplicate request logic must be enforced server-side, not by bot memory
all admin mutation endpoints must create admin_action_logs
all verification failures should write token_verification_attempt_logs where relevant
all delivery failures should write token_usage_logs with zero quota deduction

---

**Insert below `### DEP-12.`**

```markdown
### DEP-13. Signed Delivery Payload Validation
Required before multi-bot production delivery so the primary bot can issue short-lived signed download payloads and the delivery bot can verify them safely before sending files.
---

# =========================================================
# SEC-09. PHASES
# =========================================================

## Phases

### PH-01. Foundation MVP
Target:
- plans
- tokens
- linked accounts
- quota logic
- core validation
- secure token handling

Modules:
- M01
- M02
- M03
- M05
- part of M10

### PH-02. Transfer and Recovery
Target:
- add account
- replace account
- lost device recovery
- transfer code flow

Modules:
- M04
- part of M11

### PH-03. Payments and Activation
Target:
- Telegram Stars
- local manual payment
- OCR-assisted review
- admin approval flow

Modules:
- M07
- part of M09
- part of M12

### PH-04. Reporting and Audit
Target:
- admin history
- user history
- traceable logs
- operational visibility

Modules:
- M06
- part of M10
- part of M11

### PH-05. Language and UX Refinement
Target:
- Burmese-first UX
- English toggle
- multilingual content structure
- cleaner menus and messages

Modules:
- M08
- part of M11
- part of M12

### PH-06. Advanced Controls
Target:
- future anti-abuse
- advanced notifications
- family plan logic
- promotional flows
- analytics expansion

Modules:
- future queue promotions

### PH-07. Legacy Discovery and Staging
Target:
- inspect legacy schema and logic
- classify data
- prepare PostgreSQL target mapping
- build staging import and cleanup flow

Modules:
- M13
- part of M10
- part of M06

### PH-08. Migration and Cutover
Target:
- import normalized data into PostgreSQL
- validate entitlement parity
- validate media delivery references
- switch traffic to the new environment
- maintain rollback-safe legacy read-only window

Modules:
- M13
- part of M02
- part of M06
- part of M09
- part of M10

## Module 15. Backend Implementation Blueprint (Node.js)

### M15-F01. Tech Stack

- Runtime: Node.js (LTS)
- Framework: Express.js (or Fastify optional)
- Database: PostgreSQL
- ORM/Query: Prisma (recommended) or Knex
- Auth: Service key (internal), session (admin)
- Deployment: VPS (VPS-1 → VPS-2 migration ready)

---

### M15-F02. Project Structure

Recommended structure:

/src
  /config
  /db
  /modules
    /auth
    /token
    /request
    /delivery
    /payment
    /admin
    /search
  /middleware
  /utils
  /jobs
  /routes
  app.js

---

### M15-F03. Module Responsibilities

auth:
- service key validation
- request authentication

token:
- token validation
- linking logic
- expiry checks

request:
- request validation
- duplicate protection
- commit success/failure

delivery:
- payload signing/verification
- delivery validation

payment:
- telegram stars webhook
- manual payment handling

admin:
- plan management
- token management
- logs

search:
- file search + metadata

---

### M15-F04. Controller → Service Flow

Example:

POST /api/v1/requests/validate

Flow:
- request.controller
- request.service.validateRequest()
- token.service.checkLinkedUser()
- quota.service.checkQuota()
- duplicate.service.checkDuplicate()
- return response

---

### M15-F05. Critical Transaction Logic

Commit success must be atomic:

Within single DB transaction:
1. insert usage log
2. decrement token quota
3. update daily_usage_counters

If any step fails:
- rollback entire transaction

---

### M15-F06. Middleware Layer

Required middleware:

- serviceAuthMiddleware
- requestLoggerMiddleware
- errorHandlerMiddleware
- rateLimiter (basic)
- validationMiddleware (schema-based)

---

### M15-F07. Delivery Payload System

- use signed payload (JWT or HMAC)
- include:
   - request_id
   - token_id
   - expiry timestamp

Rules:
- short-lived (≤ 3 minutes)
- validated by backend before delivery
- one-time or guarded use

---

### M15-F08. Retry & Job Handling

- retry delivery up to 3 times
- use simple retry loop (Phase 1)
- optional future:
   - queue system (BullMQ)

Admin notification trigger:
- send failure
- abnormal error

---

### M15-F09. Logging Strategy

Log types:

- request logs
- token verification logs
- payment logs
- admin logs
- error logs

Rules:
- do not overwrite logs
- append-only for audit-critical logs

---

### M15-F10. Environment Config

.env structure:

- DATABASE_URL=
- SERVICE_KEY_PRIMARY_BOT=
- SERVICE_KEY_DELIVERY_BOT=
- SERVICE_KEY_WEBAPP=
- JWT_SECRET=
- TOKEN_HASH_SECRET=
- APP_ENV=production/staging

---

### M15-F11. Phase 1 Build Order

1. Setup project + DB connection
2. Implement auth middleware
3. Implement token validation module
4. Implement request validation
5. Implement commit success logic
6. Implement delivery payload system
7. Implement search endpoints
8. Implement payment endpoints
9. Implement admin endpoints
10. Add logging + error handling

---

### M15-F12. Phase 1 Constraints

- single server (no microservices)
- no queue system required initially
- no caching layer required initially
- keep logic centralized

---

### M15-F13. Future Expansion Ready

- queue system (BullMQ)
- Redis caching
- multi-instance scaling
- load balancer
- analytics dashboard

## Module 16. VPS-1 Backup and Data Migration Strategy

### M16-F01. Migration Philosophy

System migration must NOT be treated as direct database restore.

Rules:
- new system uses different schema and logic
- old data must be transformed before import
- migration must preserve:
   - tokens
   - user associations
   - usage history (if possible)
   - payment records

Purpose:
- ensure clean transition without corrupting new system design

---

### M16-F02. VPS-1 Backup Requirements

Before any implementation:

Create full backup of VPS-1:

1. Database dump
   - full SQL dump
   - include all tables

2. File storage (if applicable)
   - media references
   - metadata

3. Bot configuration
   - environment variables
   - tokens

Rules:
- store backup securely
- keep at least 2 copies
- do not overwrite original

---

### M16-F03. Old System Data Analysis

Identify:

- tables and structure
- token format
- user linkage model
- request logs
- payment records

Output:
- data inventory document

---

### M16-F04. Data Mapping Strategy

Define mapping between old and new system:

Examples:

- old_tokens → tokens
- old_users → token_linked_accounts
- old_requests → token_usage_logs

Rules:
- map only necessary data
- discard corrupted or irrelevant data
- normalize data into new schema

---

### M16-F05. Migration Script

Implementation:

- create one-time migration script
- read old DB
- transform data
- insert into new DB

Rules:
- do not bypass backend logic for critical fields
- preserve audit integrity
- log all migration actions

---

### M16-F06. Migration Validation

After import:

- verify token counts
- verify quota values
- verify linked accounts
- verify sample request logs

---

### M16-F07. Rollback Strategy

If migration fails:

- restore VPS-1 system
- do not partially switch users

Rules:
- migration must be reversible
- never overwrite original data

---

### M16-F08. Migration Execution Plan

Steps:

1. Backup VPS-1
2. Setup VPS-2 (new system)
3. Run migration script
4. Validate data
5. Switch bot to new backend
6. Monitor system

---

### M16-F09. Risks

RSK-MIG-01:
- data mismatch between systems

RSK-MIG-02:
- lost quota or incorrect balances

RSK-MIG-03:
- user confusion after migration

Mitigation:
- validation checks
- admin manual adjustment tools
- clear user messaging

---

# =========================================================
# SEC-10. DEPENDENCIES
# =========================================================

## Dependencies

### DEP-01. Core Token Engine
Required before request enforcement, payments, and history.

### DEP-02. Linked Account Engine
Required before transfer/recovery and multi-account enforcement.

### DEP-03. Payment Review Workflow
Required before manual payment activation logic.

### DEP-04. Audit Logging Layer
Required before advanced admin reporting and dispute handling.

### DEP-05. Message Content Layer
Required before multilingual scaling and consistent UI text control.

### DEP-06. Legacy Data Backup Set
Required before migration work begins. Must include legacy SQLite DB, code snapshot, env/config snapshot, and service definitions.

### DEP-07. PostgreSQL Target Schema
Required before staging import, mapping validation, and constraint enforcement.

### DEP-08. Legacy-to-Target Mapping Rules
Required before member, payment, media, and analytics import logic can be finalized.

### DEP-09. Delivery Reference Validation
Required before cutover to confirm inherited Telegram source references remain usable on the new system.

### DEP-10. Backend API Layer
Required so the Telegram bot depends on backend APIs for:
- token validation
- quota checks
- linked-account checks
- usage logging
- payment state lookup

### DEP-11. WebApp Admin Layer
Required before authoritative member management, payment review, quota adjustment, and support operations can be considered complete.

### DEP-12. Atomic Entitlement Transaction Layer
Required before production release so quota deduction, daily counter update, and usage logging succeed or fail together. This prevents double deduction, partial writes, and quota drift under concurrent requests.

### DEP-13. Backend API Enforcement Layer

All business rules must be enforced via backend API.

Bot and WebApp must act as clients only.

Required before:
- production deployment
- multi-bot setup
---

# =========================================================
# SEC-11. RISKS
# =========================================================

## Risks

### RSK-01. Token Abuse Risk
Risk:
- token sharing beyond intended usage

Mitigation:
- linked-account slot limits
- logging
- revoke/reissue
- future anti-abuse controls

### RSK-02. OCR Reliability Risk
Risk:
- screenshot OCR may be inaccurate or manipulated

Mitigation:
- OCR as assistant only
- admin review
- review logs

### RSK-03. Scope Creep Risk
Risk:
- too many advanced features too early

Mitigation:
- phase-by-phase planning
- strict module boundaries
- queue-first approach

### RSK-04. Data Complexity Risk
Risk:
- poor schema causes reporting and workflow pain later

Mitigation:
- proper database planning
- traceable entities
- logging-first mindset

### RSK-05. Entitlement Carry-Over Risk
Risk:
- active members may lose time, quota continuity, or status accuracy during migration

Mitigation:
- recompute entitlement from authoritative dates
- preserve legacy references
- validate active user samples before cutover

### RSK-06. Delivery Reference Risk
Risk:
- inherited Telegram message references may fail on the new environment if channel access or message integrity differs

Mitigation:
- sample delivery validation
- fallback remediation queue
- do not decommission legacy infrastructure before parity confirmation

### RSK-07. Legacy Security Debt Risk
Risk:
- insecure legacy patterns may be copied into the new system

Mitigation:
- PostgreSQL target redesign
- hashed token storage
- foreign key enforcement
- secured admin exposure
- migration-specific security review

### RSK-08. Data Mapping Risk
Risk:
- weakly typed legacy SQLite fields and orphan rows may import incorrectly into normalized PostgreSQL structures

Mitigation:
- staging cleanup
- typed transformation rules
- rejection logging
- import audit tables

### RSK-09. Hardcoded Infrastructure Naming Risk
Risk:
- personal labels such as VPS-1 and VPS-2 may accidentally leak into code, config, or logic and reduce portability

Mitigation:
- enforce environment-based configuration
- use role-based architecture instead of personal server labels
- keep prompts and code deployment-agnostic

### RSK-10. Split Authority Risk
Risk:
- business state may become inconsistent if Telegram and WebApp both act as separate authorities

Mitigation:
- WebApp/backend as source of truth
- bot reads and enforces backend state only
- audit all admin-side modifications centrally

### RSK-11. Concurrent Quota Deduction Risk
Risk:
- simultaneous requests from linked accounts may cause double deduction, stale daily-cap checks, or mismatched remaining quota if updates are not atomic

Mitigation:
- transaction-based delivery commit
- row-level locking or equivalent safe concurrency control on token and daily counter rows
- duplicate guard key for short-window repeat requests
- append-only usage log before/with quota mutation trace

### RSK-12. Auto Replacement Confusion Risk

Description:
- users may not realize their account was replaced

Mitigation:
- clear notification message on replacement
- optional future: replacement history view in WebApp

### RSK-13. Redirect Payload Abuse Risk

Description:
- users may attempt to reuse or tamper with download links

Mitigation:
- signed payload with expiry
- one-time or short-lived token validation
- backend verification before file delivery

### RSK-13. Delivery Payload Replay/Tamper Risk
Risk:
- users may reuse, forward, or tamper with signed delivery links/buttons to attempt unauthorized access

Mitigation:
- short-lived signed payloads
- backend verification before delivery
- telegram_user_id binding where applicable
- one-time-use or replay-guard validation
- clear expiry handling and delivery-failure logging
---

# =========================================================
# SEC-12. FUTURE ADDITIONS QUEUE
# =========================================================

## Future Additions Queue

### Q-001. PIN or 2-Step Verification
Potential later enhancement for sensitive actions.

### Q-002. Family Plan Logic
Potential later enhancement for higher-tier shared usage logic.

### Q-003. Promotional Tokens
Potential later enhancement for campaigns or marketing offers.

### Q-004. Category-Based Restrictions
Potential later enhancement for limiting certain content by plan.

### Q-005. Analytics Dashboard
Potential later enhancement for usage, revenue, and operational insights.

### Q-006. Advanced Anti-Abuse Scoring
Potential later enhancement for suspicious activity analysis.

### Q-007. Migration Dry-Run Checker
Potential later enhancement for repeatable pre-cutover validation.

### Q-008. Media Reference Health Scanner
Potential later enhancement for checking inherited Telegram delivery references at scale.

### Q-009. Legacy Plan Retirement Workflow
Potential later enhancement for converting legacy carried-over users into fully native plan structures on renewal.

### Q-010. Self-Service Migration Status Checks
Potential later enhancement for letting users check migration-related account status where appropriate.

### Q-011. Post-Migration Analytics Parity Dashboard
Potential later enhancement for comparing old and new operational metrics after cutover.

---

# =========================================================
# SEC-13. PROMPT SOURCE
# =========================================================

## Prompt Source

### Prompt Use Rule
This section exists so future prompts can be generated from the implementation plan without rewriting everything.

### Prompt Types to Generate Later
- VS Code implementation prompt by phase
- VS Code implementation prompt by module
- review/audit prompt
- database design prompt
- workflow prompt
- payment logic prompt
- UI/UX prompt
- bug-fix prompt
- refactor prompt

### Prompt Generation Rule
Always generate implementation prompts from the latest updated source sections, not from outdated memory.

### Prompt Environment Rule
When generating implementation prompts:
- do not reference VPS-1 or VPS-2 as if they are machine-known identifiers
- use terms such as:
  - legacy server
  - new server
  - production environment
  - backend server
  - bot server
  - database server
- use environment variables, service roles, and deployment metadata instead of owner-friendly nicknames

### Migration Prompt Source Add
When generating migration or database prompts:
- treat legacy SQLite as source only
- target PostgreSQL for the new system
- preserve active member entitlements
- preserve payment and audit history where relevant
- validate inherited Telegram media delivery references
- normalize and clean legacy rows before production import

### Legacy Runtime Input Notes
Use legacy audit findings as authoritative migration input when such audit data is confirmed:
- Ubuntu 22.04.1 LTS
- Python 3.10
- python-telegram-bot
- aiosqlite
- SQLite media.db
- delivery via `copy_message` using `file_chat_id + file_message_id`
- active subscriptions and legacy plans preserved through migration
- movies and series index reuse preferred over re-indexing
- old short-lived delivery tokens should not drive target design

---

# =========================================================
# SEC-14. CURRENT IMPLEMENTATION FOCUS
# =========================================================

## Current Implementation Focus
- planning only
- PostgreSQL target schema
- legacy migration design
- WebApp-first member management architecture
- refine modules and phases first
- keep future build prompts consistent with this document

---

# =========================================================
# SEC-15. FINAL PLANNING NOTE
# =========================================================

## Final Planning Note
This document is the adjustable implementation blueprint for MovieVirus. It should be updated feature by feature, module by module, phase by phase, and section by section as the product definition becomes more mature.
