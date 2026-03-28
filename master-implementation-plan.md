# MovieVirus Master Implementation Plan

# =========================================================
# A. DOCUMENT META
# =========================================================

# =========================================================
# A.1 HEADER
# =========================================================

## A.1 Header

- Project: MovieVirus
- Document Type: Master Implementation Plan
- Purpose: Single source of truth for future implementation planning, module-by-module build design, phase-by-phase rollout, and VS Code prompt generation
- Status: Active Planning Draft
- Owner: Charles

---

# =========================================================
# A.2 VERSION BLOCK
# =========================================================

## A.2 Version Block

- Version: 1.1.0
- Last Updated: 2026-03-27
- Update Method: Section-based manual update
- Update Rule: Prefer updating only the affected phase, module, feature, dependency, risk, queue item, or prompt source instead of regenerating the whole document

---

# =========================================================
# A.3 CHANGE LOG
# =========================================================

## A.3 Change Log

### A.3.1 | 2026-03-27
- Initial Master Implementation Plan created
- Added planning rules, scope, business model, modules, phases, dependencies, risks, future additions queue, and prompt source sections
- Established stable IDs for future modular updates

### A.3.2 | 2026-03-27
- Added PostgreSQL as recommended target database
- Added legacy migration planning logic
- Added database normalization, entitlement carry-over, and media index reuse guidance
- Added migration-related phases, dependencies, risks, and prompt-source rules

### A.3.3 | 2026-03-27
- Added VPS naming abstraction guidance so personal labels are not treated as implementation identifiers
- Added WebApp-first control clarification so user and member management is backend/webapp controlled, not Telegram controlled
- Improved environment-neutral wording for future implementation prompts

### A.3.4 | 2026-03-27
- Reordered document sections into cleaner planning order
- Removed duplicate migration fragments by integrating them into standard module, phase, dependency, risk, queue, and prompt sections
- Preserved stable IDs while improving scanability and future update targeting

### A.3.5 | 2026-03-27
- Refined update protocol so future implementation-plan edits must reference exact existing headings or stable IDs
- Disallowed invented placement labels when the heading does not exist in the current document
- Improved paste-ready targeting format to support easier manual updates and safer VS Code prompt preparation

### A.3.6 | 2026-03-27
- Defined structured plan tiers with quota, daily cap, and sharing limits
- Introduced controlled sharing model via max linked accounts
- Added initial plan seed configuration
- Strengthened enforcement rules for linked accounts

### A.3.7 | 2026-03-27
- Expanded Module 10 from entity list into final Phase-1 PostgreSQL schema blueprint
- Added concrete table structure for plans, tokens, members, linked accounts, usage, payments, audit, and admin control
- Added atomic entitlement transaction dependency
- Added concurrency risk and mitigation for quota correctness

### A.3.8 | 2026-03-27
- Finalized token UX (single entry, no repeat for linked users)
- Introduced automatic oldest-account replacement policy
- Set token expiry to 90 days
- Added delivery retry logic (max 3 attempts)
- Defined duplicate request protection window (30–60 seconds)
- Simplified admin model for Phase 1

### A.3.9 | 2026-03-27
- Introduced full backend API layer design
- Defined endpoint groups and responsibilities
- Implemented indirect file delivery via secondary bot
- Added duplicate protection logic
- Added retry and failure handling rules
- Added API enforcement dependency
- Added redirect payload security risk

### A.3.10 | 2026-03-27
- Added Module 14 backend API contracts with JSON-level request/response structure
- Defined search, access validation, request validation, delivery verification, commit, payment, and admin endpoints
- Added signed delivery payload dependency for indirect multi-bot file delivery
- Added replay/tamper risk coverage for short-lived delivery payloads

### A.3.11 | 2026-03-27
- Added Node.js backend implementation blueprint
- Defined project structure and module responsibilities
- Defined transaction logic and middleware layer
- Added Phase 1 build order and constraints

### A.3.12 | 2026-03-27
- Added VPS-1 backup and data migration strategy
- Defined migration as transformation process, not direct restore
- Added mapping, validation, and rollback strategy

### A.3.13 | 2026-03-27
- Added detailed migration mapping (table + field level)
- Defined transformation and loading order
- Introduced plan assignment logic
- Added migration validation steps
- Added risk for incorrect plan mapping

### A.3.14 | 2026-03-27
- Added detailed migration script plan under Module 13
- Defined staged migration runner structure for Node.js
- Added adapter-based legacy mapping approach
- Added quota reconciliation, linked-account migration, and delivery-reference migration rules
- Added required migration reporting outputs for cutover readiness

### A.3.15 | 2026-03-27
- Added quota reminder system (5, 1, 0 thresholds)
- Introduced user usage transparency API
- Added reminder tracking table
- Added notification logic and anti-spam rules
- Added reminder fatigue risk

### A.3.16 | 2026-03-27
- Updated migration strategy based on real VPS-1 system analysis
- Converted user-based subscription model to token-based entitlement
- Added plan conversion logic (expiry → quota)
- Excluded delivery_tokens from migration
- Added data cleanup and integrity correction rules
- Added entitlement conversion risk

### A.3.17 | 2026-03-27
- Expanded WebApp admin design from high-level authority rule into a full admin portal structure
- Added dashboard, plans, tokens, members, linked accounts, payments, requests, audit logs, and media library screens
- Preserved VPS-1 media management capability while moving toward unified admin control
- Added WebApp operational alerts and user transparency view guidance
- Added unified admin portal dependency and admin-portal overreach risk

### A.3.18 | 2026-03-27
- Added dynamic Telegram button system
- Defined button types and action categories
- Introduced callback payload structure
- Added backend-driven button rendering flow
- Added button configuration support for future WebApp
- Added button-state mismatch risk

### A.3.19 | 2026-03-28
- Defined backend core decision engine and deterministic enforcement order
- Replaced normal expiry-based validation with quota-first standard-plan logic
- Added token and request state machines
- Added atomic commit rules and backend response rules for UI rendering

### A.3.20 | 2026-03-28
- Added state → UX mapping system
- Introduced deterministic message_key and button_set_key binding
- Defined reusable button sets
- Centralized UI decision logic in backend
- Added state-to-UX desynchronization risk

### A.3.21 | 2026-03-28
- Added admin configuration system
- Introduced dynamic message, button, and plan control via DB
- Defined runtime resolution rules for configuration
- Added admin system module (M15)
- Added admin audit logging
- Added misconfiguration risk and mitigation

### A.3.22 | 2026-03-28
- Added admin operation playbook (M15-F06)
- Defined daily admin workflows and support cases
- Defined system monitoring and abuse detection
- Defined admin action rules and communication standards
- Added audit and emergency handling procedures
- Added operational risks and mitigation

### A.3.23 | 2026-03-28
- Finalized quota-based non-expiring plan model
- Introduced plan_type and nullable duration_days
- Updated upgrade formula to carry-forward + add model
- Removed downgrade scheduling logic
- Added token exposure security rules
- Added linked-account replacement cooldown
- Removed quota_restored from request state machine
- Added system health state
- Added payment expiry logic
- Simplified delivery payload model
- Added migration clarifications (200 users)
- Fixed structural inconsistencies (IDs/modules)

---

# =========================================================
# A.4 UPDATE PROTOCOL
# =========================================================

## A.4 Update Protocol

Use this document as the implementation planning source.
Future updates should follow these rules:

1. Do not rewrite the whole document unless explicitly requested.
2. Update only the relevant phase, module, feature, dependency, risk, queue item, or prompt source.
3. Preserve numbering and IDs where possible.
4. Add new features under the correct module using the hierarchical numbering format.
5. Add new phases using the format `D.x`.
6. Add dependencies using the format `E.x`.
7. Add risks using the format `F.x`.
8. Add roadmap items into the Future Additions Queue before promoting them into active implementation sections.
9. Update the Change Log whenever a meaningful change is made.
10. Generate VS Code prompts from this document only after source planning sections are updated.
11. Prefer integrating updates into the correct standard section instead of appending detached add-on blocks.
12. When giving update instructions, always reference exact existing section names, headings, or stable IDs that already exist in the current document.
13. Do not use invented placement labels such as "Admin Section", "Infrastructure Section", or similar unless those exact headings already exist in the current document.
14. If adding new text between existing sections, specify the insertion point using the nearest real heading or ID, such as:
    - "insert below `### A.4`"
    - "insert below `### C.9.4`"
    - "insert above `## D. Phases`"
15. If the exact insertion point cannot be confirmed from the current document text, say so honestly and provide the update as:
    - target section name
    - nearest confirmed heading/ID
    - paste-ready text
    Do not pretend an unverified heading exists.

---

# =========================================================
# A.5 PLANNING RULES
# =========================================================

## A.5 Planning Rules

### A.5.1 Implementation Planning Principle
This document is for future implementation planning, not for storing GPT behavior rules. It defines what to build, in what order, with what logic, and under which technical and operational rules.

### A.5.2 Source Separation Rule
- Master Instruction Source = GPT thinking and update behavior
- Master Implementation Plan = build blueprint and future implementation logic

### A.5.3 Modularity Rule
Every major implementation area should be organized into modules, features, phases, dependencies, and risks.

### A.5.4 Incremental Rule
Build should be planned phase by phase, not as one giant implementation.

### A.5.5 Traceability Rule
Important technical, workflow, and business decisions should remain traceable through versioning, change logs, dependencies, and risk notes.

---

# =========================================================
# B. PRODUCT DEFINITION AND BUSINESS LOGIC
# =========================================================

# =========================================================
# B.1 PRODUCT VISION
# =========================================================

## B.1 Product Vision

MovieVirus is a token-based Telegram file request and delivery platform designed to support scalable subscription access, linked Telegram accounts, flexible recovery and transfer flows, payment review, reporting, auditability, multilingual user experience, and future feature expansion.

The system should be:
- scalable
- secure
- fair
- support-friendly
- traceable
- modular
- future-proof

---

# =========================================================
# B.2 SCOPE
# =========================================================

## B.2 Scope

### B.2.1 In Scope
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

### B.2.2 Out of Scope for Initial Build
- advanced anti-abuse scoring
- full automatic OCR payment approval
- complex family plan billing logic
- heavy analytics dashboards
- advanced content recommendation engine
- hardware fingerprinting
- commercial-grade identity verification

---

# =========================================================
# B.3 CORE BUSINESS LOGIC
# =========================================================

## B.3 Core Business Logic

### B.3.1 Core Model
- Token = subscription entitlement
- Telegram account = linked access session
- Database = enforcement, reporting, and audit layer

### B.3.2 Plan Logic
Each plan should usually define:
- price
- total quota
- daily cap
- duration/expiry
- max linked Telegram accounts

### B.3.3 Usage Logic
- one successful file delivery consumes one quota unit
- failed token validation should not consume quota
- file not found should not consume quota
- bot/send failure should not consume quota
- duplicate requests within a short safe window may avoid double deduction
- admin may manually restore quota when justified

### B.3.4 Linked Account Logic
- if Telegram account is already linked, allow normal validation
- if not linked and free slot exists, auto-link
- if max linked accounts is reached, deny new linkage unless replacement/reset/admin policy allows it

### B.3.5 Upgrade/Downgrade Logic
- upgrade = immediate with fair recalculation
- Downgrade logic removed. Users purchase new plan instead of downgrade.

### B.3.6 Payment Logic
- support Telegram Stars and local manual payment
- for local manual payment screenshots, OCR should assist review, not replace approval in phase 1

### B.3.7 Management Authority Logic
- user and member management is controlled from the WebApp and backend
- Telegram is not the source of truth for plans, quota, linked accounts, or token lifecycle
- Telegram acts as request, validation, and delivery interface only

### B.3.8 Infrastructure Naming Logic
- labels such as VPS-1 and VPS-2 are owner-friendly names only
- implementation must use environment-based or role-based identifiers instead of personal server nicknames

### B.3.9 Legacy Migration Logic
For legacy transition:
- PostgreSQL is the recommended target database
- legacy SQLite data should be treated as source input, not as the target schema design
- active subscriptions must remain valid through their carried-over entitlement period
- valid media index data should be reused when delivery references remain operational
- expired or already used short-lived delivery tokens should not be migrated as active target tokens
- insecure legacy storage patterns must be removed during migration

---

# =========================================================
# C. MODULES
# =========================================================

# =========================================================
# C.1 SUBSCRIPTION PLANS AND TOKEN ENTITLEMENT
# =========================================================

## C.1 Module 01: Subscription Plans and Token Entitlement

### C.1.1 Plan Definitions
Define:
- plan name/code
- price
- quota
- daily cap
- duration
- max linked accounts

### C.1.1.1 Default Plan Definitions (Initial Configuration)
System should support admin-defined plans.

Initial recommended plans:

Starter:
- price: 3,000 MMK
- total quota: 30
- daily cap: 3
- max linked accounts: 1

Basic:
- price: 5,000 MMK
- total quota: 50
- daily cap: 5
- max linked accounts: 2

Plus:
- price: 10,000 MMK
- total quota: 100
- daily cap: 10
- max linked accounts: 3

Pro:
- price: 15,000 MMK
- total quota: 150
- daily cap: 15
- max linked accounts: 4

Premium:
- price: 20,000 MMK
- total quota: 200
- daily cap: 20
- max linked accounts: 5

Notes:
- These are default presets only
- Admin can modify or create new plans dynamically
- Standard plans do not expire by time
- Optional expiry is reserved only for special-case plans, promos, or manual override scenarios

### C.1.2 Token Statuses
Suggested statuses:
- Active
- Pending Activation
- Expired
- Suspended
- Revoked
- Exhausted

### C.1.3 Upgrade and Downgrade Policy
- upgrade = immediate
- Downgrade logic removed. Users purchase new plan instead of downgrade.

---

# =========================================================
# C.2 FILE REQUEST AND QUOTA ENFORCEMENT
# =========================================================

## C.2 Module 02: File Request and Quota Enforcement

### C.2.1 Token & Linked Account Validation Engine
Validation must prioritize linked account recognition over repeated token input.

Core Logic:
1. Check if telegram_user_id is linked to any token:
   - IF linked:
       → use linked token
       → skip token input
   - ELSE:
       → request token
       → validate token
       → link account if slot available or replace oldest according to policy
2. Enforce in exact order:
   - token existence
   - token status
   - total quota remaining
   - daily cap remaining
   - linked account eligibility
   - duplicate guard pre-check when relevant
3. Linking rules:
   - auto-link if slot available
   - auto-replace oldest if full and policy allows it
4. Standard plans must not depend on time-based expiry checks.
5. Optional expiry checks are allowed only for explicitly configured special-case entitlements.

Purpose:
- remove repeated token entry
- enforce fairness via quota + daily cap + controlled sharing
- keep backend logic deterministic

### C.2.2 Validation Rule
Check:
- token status
- expiry
- total quota remaining
- daily cap remaining
- linked-account eligibility

### C.2.3 Fair Use Protection
- no deduction on failed validation
- no deduction on file not found
- no deduction on send failure
- duplicate protection window

### C.2.4 Backend Core Decision Engine
The backend must be the only authority for entitlement decisions.

Decision order per request:
1. Resolve actor
   - identify telegram_user_id
   - identify whether access comes from linked-account path or token-input path
2. Resolve entitlement
   - find token
   - reject if token missing
   - reject if status is not usable
3. Resolve quota
   - reject if total_quota_remaining <= 0
   - reject if daily cap already reached for current date
4. Resolve sharing rule
   - if user linked → continue
   - if not linked:
     - link if slot available
     - else replace oldest linked account according to plan policy
     - log replacement
5. Resolve duplicate guard
   - same token + same telegram_user_id + same file within safe window
   - return duplicate_ignored and do not deduct
6. Resolve delivery attempt
   - create request record
   - issue delivery payload
   - on final success:
     - deduct quota
     - increment daily counter
     - log delivered event
   - on failure:
     - log failure
     - do not deduct
7. Resolve post-commit reactions
   - quota reminder at 5 left
   - quota reminder at 1 left
   - exhausted action prompt at 0 left
   - user transparency history update

Purpose:
- make the request engine predictable
- keep all critical rules in one backend flow
- reduce implementation drift across modules

### C.2.5 Telegram Role Limitation
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

### C.2.6 Token State Machine
Primary token states:
- pending_activation
- active
- suspended
- revoked
- exhausted

State rules:
- pending_activation → active on successful activation
- active → exhausted when remaining quota reaches 0
- active → suspended by admin action
- active → revoked by admin action
- suspended → active by admin restore
- exhausted → active only if quota is restored or new entitlement is issued
- revoked is terminal unless explicit reissue path is used

Standard plans:
- do not transition to expired by time

Optional special-case state:
- expired may exist only for non-standard expiring entitlements if explicitly introduced later

### C.2.7 Request State Machine
Request states:
- created
- validated
- duplicate_ignored
- delivering
- delivered
- failed_validation
- file_not_found
- send_failed

Transition rules:
- created → validated after entitlement checks pass
- created → duplicate_ignored if duplicate guard triggers
- created → failed_validation if access checks fail
- validated → delivering when delivery payload is issued
- delivering → delivered on confirmed success
- delivering → send_failed after retry limit reached

Note: quota_restored is handled via quota_adjustment_logs, not as a request state.

Purpose:
- standardize audit logging
- simplify retry and dispute handling

### C.2.8 Atomic Commit Rules
The following must happen in one transaction after confirmed successful delivery:
1. insert success usage log
2. decrement token remaining quota by 1
3. upsert daily_usage_counters for the current date
4. trigger reminder threshold evaluation flags

If any part fails:
- rollback everything
- do not leave partial quota mutation

Rules:
- failed validation never deducts
- duplicate ignored never deducts
- send failure never deducts
- admin correction must use separate adjustment logs, not silent overwrite

### C.2.9 Upgrade Calculation Rule
When upgrading:
- remaining_old = total_old - used_old
- new_remaining = new_plan_total + remaining_old

Must log:
- quota_adjustment_delta = remaining_old

Store in:
- subscription_plan_change_logs

---

# =========================================================
# C.3 LINKED ACCOUNTS / DEVICE SLOTS
# =========================================================

## C.3 Module 03: Linked Accounts / Device Slots

### C.3.1 Request Flow Implementation
1. User selects file
2. System checks access path:
   IF telegram_user_id is linked:
      → continue
   ELSE:
      → request token
      → validate token
      → link account if allowed
3. Validate in backend:
   - token status
   - total quota remaining
   - daily cap
   - linked account rule
   - duplicate request window
4. Process:
   - send delivery link / secondary-bot handoff
   - retry delivery up to 3 times if needed
5. Commit on confirmed success only:
   - log usage
   - deduct quota
   - update daily counter
   - trigger reminder threshold checks
6. Handle failures without deduction:
   - validation failure
   - file not found
   - delivery failure after retries
   - duplicate ignored
7. Return clear user-facing status and matching button set

### C.3.1.1 Quota Reminder & User Awareness Flow
System must proactively inform users about remaining quota.

Trigger Conditions:
- when remaining quota = 5 → send reminder
- when remaining quota = 1 → send urgent reminder
- when remaining quota = 0 → show upgrade / resubscribe prompt

User Interaction:
- message must include:
   - remaining quota
   - plan name
   - quick action buttons:
      - "Check Usage"
      - "Upgrade Plan"
- user may ignore reminders (non-blocking)

Purpose:
- improve transparency
- increase conversion
- reduce confusion

### C.3.1.2 Dynamic Button System (Telegram UX)
All Telegram buttons must be dynamically generated by backend based on context.

Rules:
- messages MUST NOT contain hardcoded buttons
- backend decides:
   - which buttons to show
   - button labels (via message keys)
   - button actions (callback or deep link)

Button Types:
1. Navigation Buttons
   - Search Movies
   - Search Series
   - My Plan
   - Buy Plan
   - Help
2. Action Buttons
   - Request File
   - Confirm Request
   - Cancel
3. Plan Buttons
   - Starter / Basic / Plus / Pro / Premium
   - Upgrade Plan
   - Buy Plan
4. Status-Based Buttons
   - when quota exhausted → show:
      - Buy Plan
      - Upgrade Plan
   - when token required → show:
      - Enter Token
      - Buy Plan
5. Utility Buttons
   - Back
   - Refresh
   - View Usage

Rules:
- buttons must always match current system state
- avoid showing irrelevant actions
- limit number of buttons per message for readability

### C.3.2 Naming Rule
Use:
- Linked Accounts
- Allowed Accounts
- Device Slots

### C.3.3 State → UX Mapping (Message + Button Binding)
All backend states must deterministically map to:
- message_key
- button_set_key

This mapping must be centralized and consistent across all endpoints.

---

#### Core Mapping Structure
Each system state must define:

STATE:
- internal backend status

OUTPUT:
- message_key
- button_set_key

---

#### Mapping Table (Phase 1)

##### 1. ACCESS / TOKEN
STATE: token_required
→ message_key: ASK_TOKEN
→ button_set: TOKEN_ENTRY

STATE: token_invalid
→ message_key: TOKEN_INVALID
→ button_set: TOKEN_RETRY

STATE: token_linked_success
→ message_key: TOKEN_LINKED_SUCCESS
→ button_set: MAIN_MENU

---

##### 2. PLAN / ACCESS CONTROL
STATE: no_active_plan
→ message_key: NO_ACTIVE_PLAN
→ button_set: PLAN_PURCHASE

STATE: quota_exhausted
→ message_key: QUOTA_EXCEEDED_WITH_ACTION
→ button_set: PLAN_ACTIONS

STATE: daily_limit_reached
→ message_key: DAILY_LIMIT_REACHED
→ button_set: PLAN_ACTIONS

---

##### 3. REMINDERS
STATE: quota_5_left
→ message_key: REMINDER_5_LEFT
→ button_set: PLAN_ACTIONS

STATE: quota_1_left
→ message_key: REMINDER_1_LEFT
→ button_set: PLAN_ACTIONS

STATE: quota_0_left
→ message_key: REMINDER_0_LEFT
→ button_set: PLAN_PURCHASE

---

##### 4. REQUEST FLOW
STATE: request_confirm
→ message_key: REQUEST_CONFIRM
→ button_set: REQUEST_CONFIRM

STATE: request_processing
→ message_key: REQUEST_PROCESSING
→ button_set: NONE

STATE: duplicate_ignored
→ message_key: ERROR_RETRY
→ button_set: BACK

---

##### 5. DELIVERY
STATE: delivery_success
→ message_key: DOWNLOAD_BUTTON
→ button_set: DOWNLOAD_ACTION

STATE: delivery_failed
→ message_key: DELIVERY_FAILED
→ button_set: RETRY_ACTION

---

##### 6. PAYMENT
STATE: plan_select
→ message_key: PLAN_SELECT
→ button_set: PLAN_LIST

STATE: payment_submitted
→ message_key: PAYMENT_SUBMITTED
→ button_set: NONE

STATE: payment_approved
→ message_key: PAYMENT_APPROVED
→ button_set: MAIN_MENU

STATE: payment_rejected
→ message_key: PAYMENT_REJECTED
→ button_set: PLAN_PURCHASE

---

##### 7. STATUS / TRANSPARENCY
STATE: view_plan
→ message_key: CURRENT_PLAN
→ button_set: PLAN_ACTIONS

STATE: view_usage
→ message_key: STATUS_HISTORY
→ button_set: BACK

---

#### Rules
- every state MUST map to exactly one message_key
- every state MUST map to one button_set (or NONE)
- no conditional UI logic should exist outside backend
- frontend (bot) must only render what backend returns

Purpose:
- eliminate UI inconsistency
- ensure predictable behavior
- simplify debugging and support

### C.3.4 Same Person Policy
Do not try to prove same-human identity. Enforce slot policy only.

---

# =========================================================
# C.4 ACCOUNT TRANSFER, REPLACEMENT, AND RECOVERY
# =========================================================

## C.4 Module 04: Account Transfer, Replacement, and Recovery

### C.4.1 Add New Account
Allow when free slot exists.

### C.4.2 Replace Account
Allow according to plan or policy if slots are full.

### C.4.3 Lost Device Recovery
Support admin reset and optional limited self-reset later.

### C.4.4 Transfer Code Flow
Allow one-time short-lived transfer code from current linked account to a new account.

### C.4.5 Delivery Deletion Mechanism
Implementation:
- store message_id + delete_at
- use delayed task (setTimeout / scheduler)
- call Telegram delete API

Failure:
- log only
- no retry required (Phase 1)

---

# =========================================================
# C.5 SECURITY AND ABUSE PREVENTION
# =========================================================

## C.5 Module 05: Security and Abuse Prevention

### C.5.1 Token Security
- long random tokens
- hashed storage
- masked previews

### C.5.2 Validation Protection
- rate limiting
- cooldown/lockout
- suspicious attempt logging

### C.5.3 Recovery Security
- log linked-account additions, resets, replacements
- support revoke/reissue
- optional PIN later

### C.5.4 Payment Expiry Rule
Pending payments:
- expire after configurable window (default: 48 hours)
- notify user before expiry
- mark as expired_pending

### C.5.5 Delivery Token Model
Instead of signed payload:
- use DB-stored delivery_token
- validate via backend

Benefits:
- simpler
- supports revocation
- avoids signature complexity

#### Required Delivery Session Persistence

Because delivery uses DB-stored delivery tokens, Phase-1 schema must include a persistence model for delivery authorization.

Recommended table: `delivery_sessions`

Suggested fields:
* id (uuid, pk)
* request_key (varchar, not null, unique)
* token_id (uuid, fk -> tokens.id, not null)
* telegram_user_id (bigint, not null)
* delivery_token_hash (varchar, not null, unique)
* delivery_status (varchar, not null, default 'issued')
* expires_at (timestamptz, not null)
* consumed_at (timestamptz, nullable)
* created_at (timestamptz, not null)
* updated_at (timestamptz, not null)

Delivery status values:
* issued
* consumed
* expired
* revoked

Rules:
* delivery token must be short-lived
* delivery token must be validated by backend
* consumed delivery token must not be reusable
* replayed or expired delivery tokens must be denied and logged

---

# =========================================================
# C.6 REPORTING, HISTORY, AND AUDIT
# =========================================================

## C.6 Module 06: Reporting, History, and Audit

### C.6.1 Admin Reporting
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

### C.6.2 User Self-History
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

### C.6.3 Audit Principle
Do not silently overwrite critical data. Prefer dedicated log/history records.

### C.6.4 Migration Audit Extension
Migration-related reporting should preserve:
- old-to-new ID mapping
- migration run logs
- rejection logs
- cutover checkpoints
- parity verification evidence

---

# =========================================================
# C.7 PAYMENTS AND ACTIVATION
# =========================================================

## C.7 Module 07: Payments and Activation

### C.7.1 Payment Methods
- Telegram Stars
- local manual payment

### C.7.2 Manual Payment Flow
- choose plan
- show payment instructions
- upload screenshot
- OCR pre-check
- pending review
- approve/reject
- activate token after approval

### C.7.3 Backend API Layer (Core Design)
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

### C.7.4 Payment Statuses
- Pending
- OCR Matched
- OCR Uncertain
- Approved
- Rejected
- Refunded
- Expired Pending

#### C.7.4.1 Auth / System
- POST /internal/auth/verify-service-key

#### C.7.4.2 Token & Access
- POST /token/validate-and-link
- POST /token/validate-linked
- GET /token/status

#### C.7.4.3 File Request Flow
- POST /request/validate
- POST /request/commit-success
- POST /request/commit-failure

#### C.7.4.4 Search
- GET /search/files
- GET /search/details

#### C.7.4.5 Payment
- POST /payment/submit
- POST /payment/approve
- POST /payment/reject

#### C.7.4.6 Admin (WebApp)
- POST /admin/token/create
- POST /admin/token/update
- POST /admin/token/revoke
- POST /admin/token/adjust-quota
- GET /admin/token/logs
- GET /admin/payment/list

### C.7.5 Request Flow via API
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

### C.7.6 Secure File Delivery Design
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

### C.7.7 Duplicate Protection
Definition:
- duplicate request = same token + same telegram_user_id + same file within 30–60 seconds

Backend must:
- generate duplicate_guard_key
- reject duplicate with status:
   duplicate_ignored

Bot must:
- show user message explaining duplicate protection
- NOT deduct quota

### C.7.8 Linked Account Replacement via API
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

### C.7.9 Retry & Failure Handling
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

### C.7.10 Reminder Notification Logic
Reminder must be triggered during request lifecycle:

On successful request (after commit-success):
- check remaining quota

IF remaining_quota == 5:
   → trigger reminder type: LOW_QUOTA
IF remaining_quota == 1:
   → trigger reminder type: CRITICAL_QUOTA
IF remaining_quota == 0:
   → trigger reminder type: EXHAUSTED

Notification Delivery:
- sent via primary bot
- must include action buttons:
   - Check Usage
   - Upgrade Plan

Rules:
- do not send duplicate reminders repeatedly for same threshold
- track last reminder sent per token

Future:
- allow scheduled reminders (optional)

### C.7.11 Button Payload and Action System
Buttons must use structured payloads.

Callback Data Format:
- ACTION:PARAMS

Examples:
- SEARCH_MOVIE
- SEARCH_SERIES
- PLAN_SELECT:starter
- REQUEST_FILE:{media_id}
- CONFIRM_REQUEST:{request_id}
- BUY_PLAN
- UPGRADE_PLAN
- VIEW_USAGE
- ENTER_TOKEN

Rules:
- keep payload short (Telegram limit)
- avoid exposing sensitive data
- validate all callback inputs on backend

---

#### Button Handling Flow
1. user clicks button
2. bot sends callback to backend
3. backend:
   - validates action
   - checks token / quota / rules
   - returns:
      - message_key
      - data
      - button_set
4. bot renders:
   - message (from message system)
   - buttons (from button system)

---

#### Response Format (API)
Backend must return:
```json
{
  "message_key": "QUOTA_EXCEEDED_WITH_ACTION",
  "data": {},
  "buttons": [
    { "type": "BUY_PLAN" },
    { "type": "UPGRADE_PLAN" }
  ]
}
```

### C.7.12 Token Delivery Rule
Flow:
1. generate token
2. send plaintext via bot message
3. discard plaintext from memory
4. store only hashed token

Admin/API:
- must return masked token only

### C.7.13 Linked Account Replacement Cooldown
Add system setting:
- replacement_cooldown_seconds (default: 600)

Rules:
- applies per token
- prevents repeated replacement within cooldown window

---

# =========================================================
# C.8 MULTILINGUAL INTERFACE AND CONTENT LAYER
# =========================================================

## C.8 Module 08: Multilingual Interface and Content Layer

### C.8.1 Language Strategy
Prefer Burmese-first UI with English toggle.

### C.8.2 Content Storage Rule
Store content by message key with Burmese and English variants.

---

# =========================================================
# C.9 ADMIN CONTROLS
# =========================================================

## C.9 Module 09: Admin Controls

### C.9.1 Plan Management
- create/edit plans
- change price
- change quota
- change daily cap
- change linked account limit
- change duration

### C.9.2 Token Management
- generate token
- assign plan
- activate/deactivate token
- revoke token
- reissue token
- extend expiry
- add bonus quota

### C.9.3 Review and Recovery Controls
- inspect linked accounts
- inspect payment submissions
- approve/reject payments
- reset linked accounts
- perform manual overrides with logs

### C.9.4 WebApp Management Authority
The WebApp and backend admin system are the only authoritative places where user/member state is modified.

This includes:
- plan assignment
- quota adjustment
- token activation and revocation
- linked-account management
- payment review outcomes
- recovery and reset actions

Telegram should reflect backend state, not define it.

### C.9.5 WebApp Admin System Scope
The WebApp admin system must be the primary operational control panel for MovieVirus.

Phase 1 WebApp scope:
- dashboard overview
- plan management
- token management
- member/user lookup
- linked-account management
- payment review and approval
- quota adjustment
- request history lookup
- audit log review
- media catalog management

Rules:
- WebApp must manage both:
  - user/member administration
  - database-backed operational records
- WebApp must not be limited to media editing only
- all writes must go through backend APIs and business rules
- WebApp must not bypass validation by writing directly to production tables from UI logic

Purpose:
- replace fragmented Telegram-admin-only operations
- centralize support, audit, and control
- improve safety, traceability, and maintainability

### C.9.6 WebApp Navigation Structure
Recommended primary navigation:
1. Dashboard
2. Plans
3. Tokens
4. Members
5. Linked Accounts
6. Payments
7. Requests / Usage Logs
8. Audit Logs
9. Media Library
10. System / Settings

Rules:
- navigation should be simple and support-friendly
- high-frequency operational screens must be reachable within one or two clicks
- search and filter controls should exist on all large-list pages
- Burmese-first labels with English toggle should follow overall language strategy

### C.9.7 Dashboard Design
Dashboard must show operational summary cards and quick actions.

Recommended dashboard widgets:
- active tokens count
- pending payments count
- exhausted tokens count
- expiring-soon tokens count
- recent failed deliveries
- recent linked-account replacements
- low-quota tokens needing attention
- quick actions:
  - create token
  - review payment
  - find member
  - adjust quota

Purpose:
- give admin immediate visibility
- reduce support response time
- surface operational risks quickly

### C.9.8 Plans Management Screen
Plans screen must support:
- create new plan
- edit existing plan
- activate/deactivate plan
- change:
  - name
  - code
  - price_mmk
  - price_stars
  - total_quota
  - daily_cap
  - duration_days
  - max_linked_accounts
  - sort_order

Rules:
- plan edits must not silently rewrite historical token snapshots
- changes apply to future token creation unless explicit migration action is taken
- all plan mutations must create admin_action_logs

### C.9.9 Tokens Management Screen
Tokens screen must support:
- search by token masked preview
- search by member or Telegram user
- view token status and plan
- create token
- activate token
- suspend/revoke token
- extend expiry
- adjust quota
- reissue token
- inspect linked accounts
- inspect payment/source history
- inspect request history

Recommended token detail panel:
- token masked preview
- plan snapshot
- remaining quota
- daily cap remaining
- expiry
- linked accounts list
- recent usage
- payment/source info
- quota adjustment history
- plan change history

Rules:
- plaintext token must never be shown after creation
- masked preview only in list/detail views
- privileged actions require confirmation

### C.9.10 Members Screen
Members screen must support:
- search by Telegram user ID
- search by username
- search by phone or payment reference where available
- view owned tokens
- view request history
- view linked-account history
- view payment history
- view language preference
- view support notes

Rules:
- member profile is support-facing identity context
- member records must not replace token-based entitlement enforcement
- admin can add notes but note changes must be auditable

### C.9.11 Linked Accounts Screen
Linked Accounts screen must support:
- search by token
- search by Telegram user ID
- view active and replaced accounts
- manually remove/reset account links
- inspect replacement history
- inspect first linked time and last used time

Rules:
- replacement/removal actions must create token_account_change_logs
- screen must clearly distinguish:
  - active
  - replaced
  - removed
  - blocked
- admin must be able to understand why a user lost access

### C.9.12 Payments Screen
Payments screen must support:
- list pending manual payments
- view OCR result/precheck
- approve/reject payment
- inspect payment history
- filter by method, status, plan, date
- open linked token/member after approval

Rules:
- payment review actions must write payment_review_logs
- final approval/rejection must write admin_action_logs
- approved payment should generate or reveal send-ready token result through backend workflow

### C.9.13 Requests and Usage Screen
Requests / Usage screen must support:
- search by token
- search by Telegram user
- filter by status
- filter by date range
- inspect:
  - requested file
  - request status
  - quota delta
  - requested_at
  - delivered_at
  - failure reason
- open related token/member from each row

Purpose:
- support transparency
- support dispute handling
- support quota restoration decisions

### C.9.14 Audit Logs Screen
Audit Logs screen must support:
- list admin actions
- filter by admin, entity type, action type, date range
- inspect before_json and after_json
- inspect quota adjustments
- inspect payment review outcomes
- inspect linked-account changes

Rules:
- audit logs must be read-only from UI
- logs must be append-only at system level
- sensitive views should be permission-restricted even in single-admin phase if future multi-admin expansion is enabled

### C.9.15 Media Library Management Screen
Media Library screen must support:
- search movies and series
- inspect source Telegram references
- edit metadata
- mark invalid references
- bulk update metadata
- review migration/import integrity issues

Purpose:
- preserve the useful VPS-1 media-editing capability
- move it into the unified admin portal instead of keeping a separate media-only control surface

### C.9.16 WebApp Permission Model (Phase 1)
Phase 1 default:
- single admin account

Rules:
- system may operate with one admin initially
- backend and UI must still be structured so future role expansion is possible
- future roles may include:
  - super_admin
  - finance_admin
  - support_admin
  - reviewer

Purpose:
- keep Phase 1 simple
- avoid repainting the architecture later

### C.9.17 WebApp UI Rules
UI rules:
- Burmese-first labels with English toggle
- clear status badges for:
  - active
  - pending
  - suspended
  - expired
  - exhausted
  - revoked
- destructive actions must require confirmation
- important details should be visible without deep navigation
- all list pages should support search, filter, and pagination
- user-facing and admin-facing wording should stay consistent with backend status codes

---

# =========================================================
# C.10 DATABASE DESIGN
# =========================================================

## C.10 Module 10: Database Design

### C.10.1 Core Entities
- plans
- tokens
- token_linked_accounts
- token_usage_logs
- daily_usage_counters

### C.10.2 Extended Entities
- token_transfer_requests
- token_account_change_logs
- payment_transactions
- payment_review_logs
- subscription_plan_change_logs
- admin_action_logs
- token_verification_attempt_logs
- user_language_preferences
- notification_logs

### C.10.3 Legacy Migration Database Rule
For migration, use PostgreSQL as the target database and do not reuse the legacy SQLite schema directly as the production target design.

### C.10.4 Migration Mapping Guidance
Recommended mapping:
- users -> members
- daily_usage -> member_daily_usage
- transactions -> payments
- delivery_tokens -> access_tokens plus access_token_items when batch payload normalization is required
- movies and series -> media_assets or retained split media tables depending on final schema decision
- series_episode_map -> media_episode_map
- request_events / search_miss / ai_events -> analytics tables

### C.10.5 Normalization Rule
Before import:
- recompute member status from dates instead of trusting legacy status blindly
- preserve original legacy IDs in mapping columns
- normalize CSV batch payloads into child rows
- clean orphan rows
- normalize enums and plan references
- enforce target-side foreign keys and indexes

### C.10.6 Final Phase-1 PostgreSQL Schema Blueprint
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

### C.10.7 Delivery Integrity Rule
Validate inherited Telegram delivery references before cutover. If delivery depends on source chat/message mapping, sample verification is mandatory before decommissioning the legacy VPS.

### C.10.8 Migration Audit Tables
Maintain migration-related tables such as:
- migration_runs
- migration_row_audit
- migration_rejections
- cutover_checkpoints

### C.10.9 Core Plan and Entitlement Tables

#### Table: plans
Purpose:
- stores admin-configurable subscription plans

Fields:
- id (uuid, pk)
- code (varchar, unique, not null)
  Example: STARTER, BASIC, PLUS
- name (varchar, not null)
- description (text, nullable)
- plan_type (varchar, not null, default 'standard')
- price_mmk (integer, not null)
- price_stars (integer, nullable)
- total_quota (integer, not null)
- daily_cap (integer, not null)
- duration_days (integer, nullable)
- max_linked_accounts (integer, not null)
- is_active (boolean, default true)
- sort_order (integer, default 0)
- created_at (timestamptz, not null)
- updated_at (timestamptz, not null)

Plan type values:
- standard
- special

Constraints:
- total_quota > 0
- daily_cap > 0
- max_linked_accounts >= 1
- duration_days > 0 (when not null)

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

### C.10.10 Telegram Account and Quota Enforcement Tables

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

#### Schema Enforcement Additions: Request Idempotency and Duplicate Guard

Purpose:

* harden request lifecycle against retries, duplicate delivery commits, and race conditions

Recommended additions:

For `token_usage_logs`:
* treat `request_key` as the canonical request idempotency key
* add `duplicate_guard_key` (varchar, nullable)
* add unique(request_key)
* add index(duplicate_guard_key, created_at desc)

Rules:
* each logical request must have exactly one `request_key`
* repeated `commit-success` or `commit-failure` calls for the same `request_key` must not create duplicate quota mutations
* duplicate-window checks may use `duplicate_guard_key` + recent time window, but quota mutation idempotency must rely on unique request identity

### C.10.11 Payment, Review, and Plan Change Tables

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
- renewal
- migration_carryover
- manual_correction

Indexes:
- index(token_id, effective_at desc)

#### Payment Approval Idempotency Rule

Purpose:

* prevent one payment from generating multiple active tokens

Required constraints:

* `tokens.source_payment_transaction_id` should be unique when not null
* `payment_transactions.approved_token_id` should be unique when not null

Rules:
* approving an already-approved payment must return the existing approved token
* admin approval must be idempotent
* repeated approval attempts must not create a second token

#### Phase-1 Downgrade Clarification

Rules:
* immediate in-place upgrade is supported with fairness recalculation
* downgrade is not an in-place entitlement mutation in Phase 1
* lower-tier purchase after current entitlement exhaustion is the standard downgrade path

Purpose:
* keep implementation aligned with current business rule
* avoid accidental live-downgrade complexity in early phases

### C.10.12 Recovery, Audit, and Admin Tables

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

### C.10.13 Optional Support Tables for Phase-1 Readiness

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

### C.10.14 Relationship and Enforcement Rules
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
   - check expires_at (only for special plan_type)
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

7. On daily-cap enforcement:
   * derive `usage_date` from a single system timezone
   * recommended default timezone: Asia/Yangon
   * all daily-cap checks and daily-counter writes must use the same backend timezone source

Recommended technical standards:
- use UUID primary keys for business entities
- use timestamptz everywhere
- prefer append-only logs for audit tables
- use jsonb only for review metadata or before/after audit snapshots
- prefer database constraints and indexes over Telegram-side assumptions


### C.10.15 User Usage Transparency & Reminder Tracking

#### Table: token_reminder_logs
Purpose:
- prevent duplicate reminder spam
- track reminder history

Fields:
- id (uuid, pk)
- token_id (uuid, fk)
- reminder_type (varchar)
- triggered_at (timestamptz)
- telegram_user_id (bigint, nullable)
- created_at (timestamptz)

Reminder types:
- LOW_QUOTA
- CRITICAL_QUOTA
- EXHAUSTED

Indexes:
- index(token_id, reminder_type)

---

#### API Requirement: Usage Transparency
Users must be able to view usage history.

Endpoint:
GET /api/v1/token/usage

Response must include:
- total quota
- remaining quota
- daily usage
- list of recent requests:
   - file name
   - requested_at
   - status

Purpose:
- build trust
- allow self-check
- reduce support load

### C.10.16 Button Configuration (Future WebApp Control)
Buttons must support configuration via backend (future WebApp).

#### Table: button_templates (optional Phase 2)
Fields:
- id
- button_key
- label_key
- action_type
- action_payload_template
- sort_order
- is_active
- created_at

Purpose:
- allow admin to customize:
   - button labels
   - ordering
   - visibility

---

#### Button Set Logic (Runtime)
Backend should define button sets:

Examples:
- HOME_MENU
- SEARCH_RESULTS
- PLAN_LIST
- QUOTA_EXCEEDED
- TOKEN_REQUIRED

Each set contains:
- ordered list of button types

---

#### Example Button Set
QUOTA_EXCEEDED:
- BUY_PLAN
- VIEW_PLAN
- HELP

---

Rules:
- button sets must be reusable
- must be mapped to message_key or system state
- must support future WebApp customization

### C.10.17 Admin Configuration Data Model
System must support dynamic configuration via WebApp.

---

#### 1. message_templates
Fields:
- id
- key (e.g., QUOTA_EXCEEDED)
- lang (mm, en)
- content
- is_active
- version
- updated_by
- updated_at

Purpose:
- allow admin to edit all user-facing messages
- support multilingual system
- allow safe updates without redeploy

---

#### 2. button_templates
Fields:
- id
- button_key (e.g., BUY_PLAN)
- label_key (linked to message_templates)
- action_type (callback / link)
- action_payload_template
- sort_order
- is_active
- updated_by
- updated_at

Purpose:
- allow admin to control button labels and behavior

---

#### 3. button_sets
Fields:
- id
- set_key (e.g., PLAN_ACTIONS)
- description
- is_active
- updated_at

---

#### 4. button_set_items
Fields:
- id
- set_id
- button_key
- sort_order
- is_active

Purpose:
- define which buttons appear in each context

---

#### 5. plan_definitions
Fields:
- id
- plan_key (starter, basic, etc.)
- name
- price
- total_quota
- daily_cap
- max_linked_accounts
- is_active
- updated_by
- updated_at

Purpose:
- allow admin to change plans without code changes

---

#### 6. system_settings
Fields:
- key
- value
- description
- updated_at

Examples:
- duplicate_window_seconds = 60
- max_delivery_retry = 3
- replacement_cooldown_seconds = 600
- payment_pending_expiry_hours = 48

---

#### 7. admin_audit_logs
Fields:
- id
- admin_id
- action_type
- target_type
- target_id
- old_value
- new_value
- created_at

Purpose:
- full traceability of admin actions
- prevent silent data corruption

### C.10.18 Plan Type & Duration Handling
Add field:
- plan_type (standard | special)

Update rules:
- duration_days:
  - nullable
  - only used if plan_type = special
- entitlement logic:
  - IF plan_type = standard → ignore duration_days
  - IF plan_type = special → enforce expiry

Purpose:
- remove ambiguity in plan validation

---

# =========================================================
# C.11 USER SELF-SERVICE
# =========================================================

## C.11 Module 11: User Self-Service

### C.11.1 User Menu
- My Plan
- My Remaining Quota
- My Request History
- My Payment History
- My Linked Accounts
- Manage Linked Accounts
- Change Language
- Help / Payment Guide

### C.11.2 Linked Account Self-Service
- add new account
- replace account
- request reset
- see linked-account history

### C.11.3 User Transparency Pages via WebApp / Bot-Linked Views
Users should be able to inspect their own entitlement transparency data through supported self-service views.

Recommended self-service views:
- current plan
- token masked preview
- remaining quota
- daily remaining
- expiry date
- recent requests with date/time
- linked accounts
- payment history
- reminder / exhaustion status

Purpose:
- reduce support burden
- reinforce fairness and trust
- align user-visible data with admin-visible records

---

# =========================================================
# C.12 NOTIFICATIONS AND MESSAGING
# =========================================================

## C.12 Module 12: Notifications and Messaging

### C.12.1 User Notifications
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

### C.12.2 Admin Alerts
- suspicious payment submission
- repeated failed token attempts
- unusual account linking activity
- manual review backlog

### C.12.3 Admin WebApp Alerts
The WebApp should display operational alerts for:
- pending payment backlog
- failed delivery backlog
- repeated quota disputes
- unusual linked-account replacement frequency
- low-quota / exhausted token trends
- migration reconciliation exceptions

Purpose:
- keep operational issues visible without relying only on Telegram alerts
- support dashboard-driven administration

---

# =========================================================
# C.13 LEGACY MIGRATION AND CUTOVER
# =========================================================

## C.13 Module 13: Legacy Migration and Cutover

### C.13.1 Migration Objective
Safely migrate legacy data and active users into the new system without breaking entitlement continuity, delivery integrity, or auditability.

### C.13.2 Target Database Rule
Use PostgreSQL as the target database. Do not reuse the legacy SQLite schema directly as the production target design.

### C.13.3 Data Classification Rule
Classify legacy data before import:
- MUST migrate: active member entitlement data, payment history, daily usage baselines where relevant, movies, series, episode mapping, core media references
- SHOULD migrate: analytics and reminder history where useful
- DISCARD or REBUILD: expired/used short-lived delivery tokens, stale request placeholders, obsolete cleanup queues, invalid orphan rows

### C.13.4 Security Remediation Rule
The new system must remove insecure legacy practices such as:
- plaintext token storage
- publicly exposed dev admin services
- missing relational integrity
- weak audit preservation

### C.13.5 Cutover Rule
Migration should use:
- immutable backup
- staging cleanup
- validation import
- final delta sync
- cutover switch
- rollback-safe read-only window for legacy infrastructure

### C.13.6 Post-Cutover Verification Rule
Verify:
- entitlement parity
- payment visibility parity
- media delivery integrity
- linked-account enforcement
- quota and daily-cap correctness
- rollback readiness before final legacy shutdown

### C.13.7 Migration Script Plan
Purpose:
- move legacy VPS-1 data into the new PostgreSQL schema safely
- preserve entitlement continuity without copying insecure or obsolete legacy patterns directly

Core Script Design:
- use a one-time Node.js migration runner
- connect to:
  - legacy source database (read-only)
  - new PostgreSQL target database
- run in staged mode:
  1. discover
  2. extract
  3. normalize
  4. map
  5. load
  6. reconcile
  7. report

Rules:
- legacy source must remain read-only during migration runs
- target import must be repeatable in staging
- production migration must be logged as a named migration run
- never overwrite legacy data in place
- do not carry plaintext token storage into the new system

---

### C.13.8 Migration Script Structure
Recommended script structure:

1. `migration.config`
   - source DB connection
   - target DB connection
   - run mode: dry_run / staging_import / production_import
   - batch size
   - logging path

2. `discoverLegacySchema`
   - inspect legacy tables
   - detect missing/extra columns
   - record legacy schema snapshot for audit

3. `extractLegacyData`
   - export required source datasets
   - tokens
   - members/users
   - linked-account-like data
   - request history
   - payment history
   - delivery references where needed

4. `normalizeLegacyData`
   - clean null/invalid values
   - normalize enums
   - remove exact duplicates where safe
   - mark orphaned rows for rejection log
   - standardize timestamps and plan references

5. `mapToTargetShape`
   - transform legacy rows into target insert objects
   - preserve legacy IDs in mapping/audit fields where available
   - generate derived fields required by target schema

6. `loadTargetData`
   - insert in controlled order:
     - plans (if seed check required)
     - members
     - tokens
     - member_tokens
     - token_linked_accounts
     - token_usage_logs
     - payment_transactions
     - payment_review_logs (if migrated)
     - token_account_change_logs / quota_adjustment_logs where needed
   - use transactions per batch where safe

7. `rebuildDerivedData`
   - recompute daily_usage_counters from successful usage logs
   - recompute token status where needed
   - verify expiry and exhausted states

8. `reconcileResults`
   - compare source vs target counts
   - compare quota math
   - compare payment visibility
   - compare sample delivery references

9. `writeMigrationReport`
   - total rows processed
   - total inserted
   - total skipped
   - rejection reasons
   - warnings
   - final pass/fail recommendation

---

### C.13.9 Data Classification for Script Execution
MUST migrate:
- active tokens / active entitlement state
- plan-equivalent entitlement values
- linked Telegram account state where valid
- successful request history needed for quota correctness
- payment records
- delivery reference data required for ongoing delivery integrity

SHOULD migrate:
- member profile fields
- historical failed request logs if operationally useful
- review/audit context if available and clean

DISCARD or REBUILD:
- expired short-lived delivery payloads
- transient request placeholders
- broken orphan rows that cannot be repaired safely
- insecure legacy-only helper data not needed in target system

---

### C.13.10 Migration Batch and Idempotency Rules
Rules:
- migration must support dry-run mode
- each migration run must have unique run ID
- each imported row group must be traceable to that run ID
- rerun safety must be explicit:
  - either truncate/rebuild staging target
  - or use import markers to avoid duplicate inserts
- production import must not double-create tokens, payments, or usage logs

Recommended approach:
- staging: allow full reset and rerun
- production: use mapping tables and unique legacy-origin references

---

### C.13.11 Legacy-to-Target Mapping Adapters
Because legacy schema may differ from the new target design, script must use adapter-based mapping.

Recommended adapters:
- `tokenAdapter`
- `memberAdapter`
- `linkedAccountAdapter`
- `usageLogAdapter`
- `paymentAdapter`
- `deliveryReferenceAdapter`

Purpose:
- isolate legacy-specific mapping logic
- make migration safer if old VPS structure is inconsistent
- avoid mixing raw legacy assumptions directly into target insert logic

---

### C.13.12 Quota Reconciliation Logic
Quota correctness must be validated per token.

Required check:
- `total_quota_initial - successful_delivered_requests +/- manual_adjustments = total_quota_remaining`

Rules:
- if reconciliation fails, token must be flagged for admin review
- migration must not silently force balances to fit
- unresolved mismatches must appear in migration report

Success criteria:
- migrated remaining quota matches historical usage and adjustments
- exhausted tokens are marked correctly
- active tokens remain usable after cutover

---

### C.13.13 Linked Account Migration Rules
Rules:
- preserve valid linked Telegram accounts where confidently known
- deduplicate repeated rows by token + telegram_user_id
- if migrated linked-account count exceeds target max_linked_accounts:
  - do not silently drop rows
  - import with review flag or controlled trimming policy defined before production import
- preserve oldest-known linkage timing where possible for later replacement logic

If legacy linked-account ownership is unclear:
- migrate owner/member relationship separately from token_linked_accounts
- do not invent same-person assumptions

---

### C.13.14 Delivery Reference Migration Rules
If delivery depends on inherited Telegram source references:
- migrate source chat/message identifiers needed by delivery bot logic
- sample-verify media delivery integrity before cutover
- isolate broken references into rejection/report tables instead of importing blindly

Rules:
- broken delivery references must not block the entire migration run
- but must block final cutover if they affect active entitlement fulfillment materially

---

### C.13.15 Production Migration Execution Order
Recommended order:
1. create immutable VPS-1 backup
2. run staging discovery
3. run staging dry-run migration
4. review rejection report and quota reconciliation
5. fix adapters or mapping rules
6. rerun staging until clean enough
7. freeze legacy writes or reduce to controlled read-only window
8. take final delta backup/export
9. run production migration
10. run post-cutover verification
11. switch traffic to new backend
12. keep rollback-safe legacy window until confidence threshold is met

---

### C.13.16 Required Migration Outputs
The migration process must produce:
- migration run summary
- row-count comparison report
- rejection report
- quota reconciliation report
- linked-account exception report
- payment import report
- delivery reference validation report
- final go / no-go cutover recommendation

---

# =========================================================
# C.14 BACKEND API CONTRACTS
# =========================================================

## C.14 Module 14: Backend API Contracts

### C.14.1 API Contract Principles
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
- indirect file delivery must use short-lived payloads validated by backend before delivery

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
```

### C.14.2 Internal Client Authentication
Internal clients:
- primary Telegram bot
- delivery bot
- WebApp admin panel

Required headers:
- X-Service-Key: <server-side secret>
- X-Client-Type: primary_bot | delivery_bot | webapp
- X-Request-Id: <unique id>

Rules:
- service keys are server-side only
- user-facing Telegram clients must never see service keys
- admin login/session is separate from internal service authentication
- backend should reject requests with missing or invalid service key

Example:
```json
{
  "headers": {
    "X-Service-Key": "svc_live_xxxxx",
    "X-Client-Type": "primary_bot",
    "X-Request-Id": "req_01J..."
  }
}
```

### C.14.3 Search API

GET /api/v1/search/files

Purpose:
- search movies/series before entitlement check
- allow discovery first, then require token/purchase at request stage

Query params:
- q = required string
- year = optional integer
- subtitle = optional string
- page = optional integer
- limit = optional integer

Success example:
```json
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
```

GET /api/v1/search/details/{media_ref_id}

Purpose:
- fetch full details for one result before request

Success example:
```json
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
```

### C.14.4 Token Entry and Link API

POST /api/v1/access/validate-and-link

Purpose:
- used when requesting user is not yet linked
- validates token
- links Telegram account
- auto-replaces oldest linked account if plan limit is full

Request:
```json
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
```

Success without replacement:
```json
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
```

Success with oldest-account replacement:
```json
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
```

Common denial codes:
- INVALID_TOKEN
- TOKEN_EXPIRED
- TOKEN_SUSPENDED
- TOKEN_REVOKED
- TOKEN_EXHAUSTED
- TOKEN_DAILY_CAP_REACHED
- TOKEN_COOLDOWN_BLOCKED

### C.14.5 Linked Account Validation API

POST /api/v1/access/validate-linked

Purpose:
- used for already-linked Telegram accounts
- should not require token input again unless manually reset

Request:
```json
{
  "telegram_user_id": 123456789,
  "media_ref_id": "mov_100245",
  "media_ref_type": "movie"
}
```

Success example:
```json
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
```

Common denial codes:
- LINK_NOT_FOUND
- TOKEN_EXPIRED
- TOKEN_SUSPENDED
- TOKEN_REVOKED
- TOKEN_EXHAUSTED
- TOKEN_DAILY_CAP_REACHED

### C.14.6 Request Pre-Validation API

POST /api/v1/requests/validate

Purpose:
- validates whether a file request may proceed before delivery link is issued

Request:
```json
{
  "telegram_user_id": 123456789,
  "media_ref_id": "mov_100245",
  "media_ref_type": "movie",
  "request_context": {
    "source_chat_id": -100111222333,
    "source_message_id": 4567
  }
}
```

Success example:
```json
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
      "delivery_token": "dlp_xxxxx",
      "expires_at": "2026-03-27T12:03:00Z"
    }
  },
  "meta": null
}
```

Duplicate example:
```json
{
  "success": false,
  "code": "DUPLICATE_REQUEST_IGNORED",
  "message": "Same file was requested recently. Please wait a moment.",
  "data": {
    "duplicate_window_seconds": 45
  },
  "meta": null
}
```

Common denial codes:
- LINK_NOT_FOUND
- TOKEN_EXPIRED
- TOKEN_EXHAUSTED
- TOKEN_DAILY_CAP_REACHED
- FILE_NOT_FOUND
- REQUEST_NOT_ALLOWED

### C.14.7 Delivery Payload Verification API

POST /api/v1/delivery/verify-payload

Purpose:
- called by delivery bot before sending file
- validates DB-stored short-lived delivery token from primary bot

Request:
```json
{
  "delivery_token": "dlp_xxxxx",
  "telegram_user_id": 123456789
}
```

Success example:
```json
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
```

Denial codes:
- DELIVERY_PAYLOAD_INVALID
- DELIVERY_PAYLOAD_EXPIRED
- DELIVERY_PAYLOAD_ALREADY_USED
- DELIVERY_PAYLOAD_USER_MISMATCH

### C.14.8 Request Commit Success API

POST /api/v1/requests/commit-success

Purpose:
- called only after delivery bot successfully sends the file
- deducts quota and updates daily counter atomically

Request:
```json
{
  "request_id": "req_01J...",
  "telegram_user_id": 123456789,
  "delivery_result": {
    "delivery_chat_id": 123456789,
    "delivery_message_id": 999001,
    "delivered_at": "2026-03-27T12:01:30Z"
  }
}
```

Success example:
```json
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
```

Denial codes:
- REQUEST_NOT_FOUND
- REQUEST_ALREADY_COMMITTED
- COMMIT_CONFLICT

### C.14.9 Request Commit Failure API

POST /api/v1/requests/commit-failure

Purpose:
- called when delivery fails after up to 3 retries
- must not deduct quota
- should trigger admin notification workflow

Request:
```json
{
  "request_id": "req_01J...",
  "telegram_user_id": 123456789,
  "failure": {
    "reason_code": "SEND_FAILED_AFTER_RETRIES",
    "retry_count": 3,
    "last_error": "Telegram timeout"
  }
}
```

Success example:
```json
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

Idempotency rule:

* if the same `request_id` / `request_key` is submitted again after failure was already recorded, backend must return the existing terminal result without creating another log row that could confuse reconciliation

```

### C.14.10 Telegram Stars Payment API

POST /api/v1/payments/telegram-stars/webhook

Purpose:
- receive confirmed Stars payment result
- auto-approve and generate token immediately

Request:
```json
{
  "telegram_charge_id": "tg_01J...",
  "plan_code": "BASIC",
  "telegram_user_id": 123456789,
  "amount_stars": 500,
  "currency": "XTR"
}
```

Success example:
```json
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
```

### C.14.11 Manual Payment API

POST /api/v1/payments/manual/submit

Purpose:
- submit local manual payment proof for admin review

Request:
```json
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
```

Success example:
```json
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
```

POST /api/v1/admin/payments/{payment_transaction_id}/approve

Purpose:
- admin approval for local manual payment
- generates token and returns/send-ready token details

Success example:
```json
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
```

POST /api/v1/admin/payments/{payment_transaction_id}/reject

Purpose:
- reject local manual payment with reason

Request:
```json
{
  "reason": "Screenshot does not match payment amount."
}
```

### C.14.12 Admin Plan and Token APIs

GET /api/v1/admin/plans
POST /api/v1/admin/plans
PATCH /api/v1/admin/plans/{plan_id}

Plan response example:
```json
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
    "duration_days": null,
    "max_linked_accounts": 5,
    "is_active": true
  },
  "meta": null
}
```

POST /api/v1/admin/tokens/create
PATCH /api/v1/admin/tokens/{token_id}
POST /api/v1/admin/tokens/{token_id}/revoke
POST /api/v1/admin/tokens/{token_id}/extend-expiry
POST /api/v1/admin/tokens/{token_id}/adjust-quota
POST /api/v1/admin/tokens/{token_id}/reset-linked-accounts
GET /api/v1/admin/tokens/{token_id}/logs

Quota adjustment example:
```json
{
  "delta_quota": 5,
  "reason_code": "manual_restore",
  "notes": "Delivery failure recovery"
}
```

### C.14.13 Notifications and Status Message Contract
User-facing status codes that bot/UI should map clearly:
- INVALID_TOKEN
- TOKEN_EXPIRED
- TOKEN_SUSPENDED
- TOKEN_REVOKED
- TOKEN_EXHAUSTED
- TOKEN_DAILY_CAP_REACHED
- DUPLICATE_REQUEST_IGNORED
- TOKEN_VALIDATED_LINKED_OLDEST_REPLACED
- REQUEST_APPROVED
- REQUEST_COMMITTED
- REQUEST_FAILURE_RECORDED
- PAYMENT_SUBMITTED
- PAYMENT_APPROVED_TOKEN_CREATED
- PAYMENT_REJECTED

Rules:
- all denial reasons must be user-readable
- replacement events should notify both the incoming requester and replaced account when reachable
- send-failure events should notify requester and admin
- delivery link expiry/delete timing should be made visible to user

### C.14.14 API Idempotency and Logging Rules
Rules:
- all mutating endpoints should accept or generate a request correlation ID
- commit endpoints must be idempotent to prevent double deduction
- duplicate request logic must be enforced server-side, not by bot memory
- all admin mutation endpoints must create admin_action_logs
- all verification failures should write token_verification_attempt_logs where relevant
- all delivery failures should write token_usage_logs with zero quota deduction

### C.14.15 Core Logic Response Rules
All entitlement-related endpoints must return backend-decided state, not UI guesses.

Validation endpoints must return enough structured data to drive both message and button rendering:

Required fields where relevant:
- message_key
- status_code
- token_status
- total_quota_remaining
- daily_remaining
- linked_account_action
- duplicate_flag
- reminder_trigger
- button_set_key

Standard denial priorities:
1. invalid token / link not found
2. unusable token status
3. total quota exhausted
4. daily cap reached
5. duplicate ignored
6. delivery failure

Rules:
- standard plans should not emit expiry-based denial for normal operation
- quota and sharing state must drive primary UX
- message and button selection must be derived from backend response data

State authority rule:

* only backend services may mutate token status, payment status, linked-account state, quota counters, approved-token linkage, and delivery-session state
* bots and WebApp clients must request backend decisions and render backend-decided results only

### C.14.16 Button Set Definitions
Button sets must be predefined and reusable.
Each button_set_key maps to a list of button types.

---

#### Button Set List (Phase 1)

MAIN_MENU:
- SEARCH_MOVIE
- SEARCH_SERIES
- MY_PLAN
- BUY_PLAN
- HELP

PLAN_LIST:
- PLAN_STARTER
- PLAN_BASIC
- PLAN_PLUS
- PLAN_PRO
- PLAN_PREMIUM

PLAN_ACTIONS:
- BUY_PLAN
- UPGRADE_PLAN
- VIEW_PLAN

PLAN_PURCHASE:
- PLAN_LIST
- BACK

TOKEN_ENTRY:
- ENTER_TOKEN
- BUY_PLAN

TOKEN_RETRY:
- ENTER_TOKEN
- BACK

REQUEST_CONFIRM:
- CONFIRM_REQUEST
- CANCEL

DOWNLOAD_ACTION:
- DOWNLOAD_FILE
- BACK

RETRY_ACTION:
- RETRY
- CONTACT_SUPPORT

BACK:
- MAIN_MENU

NONE:
- (no buttons)

---

#### Rules
- button sets must be static keys, not dynamic arrays in logic
- backend selects button_set_key only
- bot resolves button_set_key into actual buttons

Purpose:
- reduce backend complexity
- standardize UX patterns
- enable WebApp-level customization later

### C.14.17 Admin Configuration Runtime Resolution
Backend must resolve configuration dynamically.

---

#### Message Resolution
IF message exists in DB (message_templates):
→ use DB version
ELSE:
→ fallback to default JSON

---

#### Button Resolution
1. backend returns button_set_key
2. system loads button_sets + button_set_items
3. system resolves:
   - button label (via message_templates)
   - action payload
4. bot renders final buttons

---

#### Plan Resolution
- backend must load plan_definitions dynamically
- no hardcoded plan logic allowed
- pricing, quota, sharing must come from DB

---

#### System Settings Resolution
- system_settings must control:
   - duplicate protection window
   - retry limits
   - replacement cooldown
   - payment pending expiry
   - optional features
- backend must read settings at runtime or cache safely

---

#### Rules
- DB overrides always take priority over code defaults
- missing config must fallback safely
- invalid config must not crash system (fallback required)

Purpose:
- allow full control without redeploy
- support rapid iteration and fixes

---

# =========================================================
# C.15 ADMIN SYSTEM (WEBAPP CONTROL LAYER)
# =========================================================

## C.15 Module 15: Admin System (WebApp Control Layer)

### C.15.1 Admin Roles (Phase 1)
- Single admin (initial phase)
- full system control

Future:
- multi-admin roles
- permission levels

### C.15.2 Editable Areas
Admin must be able to control:
1. Messages
   - edit Burmese and English content
   - enable/disable messages
2. Buttons
   - change labels
   - reorder buttons
   - enable/disable buttons
3. Plans
   - create/edit/delete plans
   - adjust price, quota, daily cap, sharing
4. System Settings
   - adjust duplicate window
   - adjust retry limits
   - toggle optional features
5. Tokens (Support Actions)
   - suspend token
   - restore quota
   - reset linked accounts

### C.15.3 UI Requirements
WebApp must provide:
- message editor (with preview)
- plan editor (form-based)
- button configuration UI
- system settings panel
- audit log viewer

### C.15.4 Safety Rules
- all changes must be logged in admin_audit_logs
- critical changes must not overwrite silently
- optional: confirmation step for high-impact changes

### C.15.5 Runtime Impact
- changes should apply immediately where safe
- no system restart required
- cached values must be refreshed periodically or invalidated

Purpose:
- empower admin to operate system without developer
- reduce downtime and dependency on code changes

### C.15.6 Admin Operation Playbook (Phase 1)
This defines how the system is operated daily and how common user issues are handled.

---

#### C.15.6.1 Daily Operations

##### C.15.6.1.1 Payment Review
Flow:
1. user submits payment
2. system marks transaction as pending/review
3. admin checks:
   - screenshot
   - OCR result (if available)
4. admin action:
   - approve → activate plan
   - reject → notify user

Rules:
- always log approval source (admin / OCR)
- never activate plan without recorded transaction

##### C.15.6.1.2 User Support Handling
Admin must handle user issues through structured steps.

---

Case A: "Quota wrong"
Steps:
1. check usage logs
2. verify:
   - successful deliveries
   - duplicate protection
3. IF system error confirmed:
   → restore quota manually
   → log action (admin_audit_logs)

---

Case B: "File not received"
Steps:
1. check request state
2. IF delivery failed:
   → confirm no quota deducted
   → ask user to retry
3. IF quota deducted incorrectly:
   → restore quota
   → log correction

---

Case C: "Token not working"
Steps:
1. verify token exists
2. check token state:
   - suspended
   - revoked
   - exhausted
3. IF linked account issue:
   → reset linked accounts OR explain replacement behavior

---

Case D: "Lost device"
Steps:
1. verify ownership (basic confirmation)
2. reset linked accounts
3. allow re-linking

Rules:
- linked account reset must NOT deduct quota
- must log reset action

##### C.15.6.1.3 Plan & Payment Issues

Case E: "Payment made but not activated"
Steps:
1. find transaction
2. verify screenshot / OCR
3. IF valid:
   → approve manually
   → activate plan
4. IF invalid:
   → reject with reason

---

Case F: "Upgrade request"
Steps:
1. confirm new payment
2. activate new plan immediately
3. old plan handling:
   - either override
   - or merge quota (based on system policy)

Rule:
- upgrade must apply immediately

---

#### C.15.6.2 System Monitoring
Admin must periodically monitor:
- delivery failures
- repeated retry failures
- unusual token usage patterns
- payment anomalies

##### C.15.6.2.1 Delivery Monitoring
IF repeated delivery failures:
→ investigate:
   - bot issues
   - Telegram limits
   - file availability

##### C.15.6.2.2 Abuse Monitoring
Signs:
- too many linked account changes
- rapid requests across multiple users

Actions:
- suspend token
- review manually

---

#### C.15.6.3 Admin Actions (Allowed Operations)
Admin can:
- restore quota
- suspend token
- revoke token
- reset linked accounts
- approve/reject payments
- modify plans
- adjust system settings

Rules:
- all actions must be logged
- no silent changes allowed

---

#### C.15.6.4 Communication Rules
All user-facing responses must:
- clearly explain reason for denial
- provide next action (buttons or guidance)
- avoid technical language

Examples:
- quota exhausted → suggest plan purchase
- token invalid → guide to re-enter or purchase

Purpose:
- reduce confusion
- reduce support load

---

#### C.15.6.5 Emergency Handling

Case G: System failure
Actions:
1. pause affected features (if possible)
2. notify users (optional broadcast)
3. investigate logs
4. restore service

---

Case H: Data inconsistency
Actions:
1. identify affected users
2. correct data via admin tools
3. log all corrections

---

Rules:
- never silently ignore issues
- always maintain audit trace

---

#### C.15.6.6 Audit & Traceability Rules
All admin actions must:
- be recorded in admin_audit_logs
- include:
   - who performed action
   - what changed
   - before/after values
   - timestamp

Purpose:
- accountability
- debugging support
- dispute resolution

### C.15.7 System Health State
System must support:
- normal
- degraded
- maintenance

Usage:
- bot changes behavior based on state
- admin dashboard displays status

Purpose:
- graceful degradation
- clearer user messaging

### C.15.8 Database Access Strategy
Use:
- Knex for queries/migrations
- raw SQL for critical transactions

Avoid:
- relying solely on ORM abstractions

### C.15.9 Admin Auth Security
Add:
- session timeout (30–60 min)
- login attempt limit
- IP logging

---

# =========================================================
# C.16 BACKEND IMPLEMENTATION BLUEPRINT (NODE.JS)
# =========================================================

## C.16 Module 16: Backend Implementation Blueprint (Node.js)

### C.16.1 Tech Stack
- Runtime: Node.js (LTS)
- Framework: Express.js (or Fastify optional)
- Database: PostgreSQL
- ORM/Query: Knex + raw SQL for critical paths
- Auth: Service key (internal), session (admin)
- Deployment: VPS (legacy → new migration ready)

### C.16.2 Project Structure
Recommended structure:
```
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
```

### C.16.3 Module Responsibilities
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
- payload storage/verification
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

### C.16.4 Controller → Service Flow
Example:
POST /api/v1/requests/validate

Flow:
- request.controller
- request.service.validateRequest()
- token.service.checkLinkedUser()
- quota.service.checkQuota()
- duplicate.service.checkDuplicate()
- return response

### C.16.5 Critical Transaction Logic
Commit success must be atomic:

Within single DB transaction:
1. insert usage log
2. decrement token quota
3. update daily_usage_counters

If any step fails:
- rollback entire transaction

### C.16.6 Middleware Layer
Required middleware:
- serviceAuthMiddleware
- requestLoggerMiddleware
- errorHandlerMiddleware
- rateLimiter (basic)
- validationMiddleware (schema-based)

### C.16.7 Delivery Payload System
- use DB-stored delivery token
- include:
   - request_id
   - token_id
   - expiry timestamp

Rules:
- short-lived (≤ 3 minutes)
- validated by backend before delivery
- one-time use enforced via DB record

### C.16.8 Retry & Job Handling
- retry delivery up to 3 times
- use simple retry loop (Phase 1)
- optional future:
   - queue system (BullMQ)

Admin notification trigger:
- send failure
- abnormal error

### C.16.9 Logging Strategy
Log types:
- request logs
- token verification logs
- payment logs
- admin logs
- error logs

Rules:
- do not overwrite logs
- append-only for audit-critical logs

### C.16.10 Environment Config
.env structure:
- DATABASE_URL=
- SERVICE_KEY_PRIMARY_BOT=
- SERVICE_KEY_DELIVERY_BOT=
- SERVICE_KEY_WEBAPP=
- DELIVERY_TOKEN_SECRET=
- TOKEN_HASH_SECRET=
- APP_ENV=production/staging

### C.16.11 Phase 1 Build Order
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

### C.16.12 Phase 1 Constraints
- single server (no microservices)
- no queue system required initially
- no caching layer required initially
- keep logic centralized

### C.16.13 Future Expansion Ready
- queue system (BullMQ)
- Redis caching
- multi-instance scaling
- load balancer
- analytics dashboard

---

# =========================================================
# C.17 VPS-1 BACKUP AND DATA MIGRATION STRATEGY
# =========================================================

## C.17 Module 17: VPS-1 Backup and Data Migration Strategy

### C.17.1 Migration Philosophy
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

### C.17.1.1 Legacy System Model Difference
VPS-1 system is fundamentally different from the new system.

Legacy Model:
- user-based subscription
- plan_id + expiry_date
- daily usage tracking
- no total quota
- no shared token model

New System Model:
- token-based entitlement
- total quota + daily cap
- max linked accounts
- controlled sharing

Migration Impact:
- users are primary entity in VPS-1
- tokens are primary entity in new system

Therefore:
- migration must convert "user subscription" → "token entitlement"
- one user may become:
   - one token
   - OR one of multiple linked accounts under a shared token

Rules:
- do NOT directly copy plan_id logic
- must reconstruct entitlement using quota-based plans

### C.17.2 VPS-1 Backup Requirements
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

### C.17.3 Old System Data Analysis
Identify:
- tables and structure
- token format
- user linkage model
- request logs
- payment records

Output:
- data inventory document

### C.17.4 Data Mapping Strategy (Revised Based on VPS-1)
Migration must transform user-based system into token-based system.

---

#### C.17.4.1 Users → Tokens + Linked Accounts
Legacy:
- users table contains subscription info

New:
For each active user:
- create ONE token
- assign:
   - plan_id (mapped)
   - total_quota (derived)
   - expiry (mapped from end_date)
- create linked account:
   - telegram_user_id → token_linked_accounts

Rule:
- 1 user = 1 token (default Phase 1 migration)
- future merging/sharing can be handled manually

---

#### C.17.4.2 Plan Conversion
Legacy:
- plan_id + expiry_date
- daily_usage only

New:
- total quota required

Conversion strategy:

Option A (recommended):
- derive quota based on remaining days × daily limit

Example:
- 10 days left × 3/day → 30 quota

Option B:
- fixed mapping per plan

All conversions must be logged.

---

#### C.17.4.3 Daily Usage → Usage Logs
Legacy:
- daily_usage (aggregated)

New:
- token_usage_logs (event-based)

Strategy:
- cannot reconstruct exact history
- create synthetic usage logs OR:
   - initialize only remaining quota

Rule:
- prioritize quota correctness over full history

---

#### C.17.4.4 Delivery Tokens → IGNORE
Legacy:
- delivery_tokens are temporary access tokens

New:
- not relevant for subscription

Rule:
- DO NOT migrate delivery_tokens

---

#### C.17.4.5 Requests / Events
Legacy:
- request_events + requests

New:
- token_usage_logs + request logs

Strategy:
- optional migration
- keep only:
   - successful deliveries (if needed)

---

#### C.17.4.6 Payments
Legacy:
- transactions table

New:
- payment_transactions

Rule:
- migrate all completed payments
- preserve:
   - amount
   - method
   - approval metadata

---

#### C.17.4.7 Media Tables
Legacy:
- movies, series, series_episode_map

New:
- media_items, episodes

Rule:
- MUST migrate
- preserve:
   - file_chat_id
   - file_message_id
   - file_unique_id

---

#### C.17.4.8 Discard Tables
Do NOT migrate:
- delivery_tokens
- message_delete_queue
- expiry_reminders (optional future)
- ai_events (optional analytics)
- search_miss (optional analytics)

---

#### C.17.4.9 Integrity Fixes During Migration
Must fix:
- orphan records
- expired but active users
- inconsistent status

Rule:
- migration must clean data, not copy errors

### C.17.4.10 Detailed Table Mapping (Old → New)
Mapping must be defined at table and field level.

#### 1. Tokens
Old → New:
- old_tokens.token → tokens.token_hash (hashed during migration)
- old_tokens.created_at → tokens.created_at
- old_tokens.expiry → tokens.expires_at
- old_tokens.quota_remaining → tokens.total_quota_remaining

Additional:
- map plan_id based on quota/price rules
- generate token_masked during migration
- set status:
   - active / expired / exhausted

---

#### 2. Users → Linked Accounts
Old → New:
- old_users.telegram_user_id → token_linked_accounts.telegram_user_id
- old_users.username → telegram_username

Rules:
- group users under correct token
- assign linked_at using earliest known usage or creation time

---

#### 3. Requests → Usage Logs
Old → New:
- old_requests.user_id → telegram_user_id
- old_requests.token → token_id
- old_requests.file_id → media_ref_id
- old_requests.status → request_status
- old_requests.created_at → requested_at

Rules:
- only successful requests deduct quota
- failed requests must have quota_delta = 0

---

#### 4. Payments
Old → New:
- old_payments.amount → amount_mmk
- old_payments.method → payment_method
- old_payments.status → payment_status
- old_payments.timestamp → created_at

Rules:
- link payment → token where possible
- otherwise keep as historical record

---

#### 5. Derived / Missing Fields
Fields not present in old system must be generated:
- token_hash → hash(old token)
- token_masked → generate masked version
- daily_usage_counters → recompute from usage logs
- duplicate_guard_key → not required for historical data

### C.17.4.11 Plan Assignment Logic
Old system may not have structured plans.

Rules to assign plan_id:

Option A (recommended):
- map based on total quota:
   - ≤30 → Starter
   - ≤50 → Basic
   - ≤100 → Plus
   - ≤150 → Pro
   - >150 → Premium

Option B:
- map based on payment amount

Fallback:
- assign default plan and log for admin review

All mappings must be logged for audit.

### C.17.5 Migration Script
Implementation:
- create one-time migration script
- read old DB
- transform data
- insert into new DB

Rules:
- do not bypass backend logic for critical fields
- preserve audit integrity
- log all migration actions

### C.17.5.1 Migration Execution Logic
Migration must run in controlled stages:

---

#### Step 1. Extract
- read old database
- export tables:
   - tokens
   - users
   - requests
   - payments

---

#### Step 2. Transform
For each dataset:

Tokens:
- hash token
- assign plan_id
- compute status

Users:
- group by token
- deduplicate telegram_user_id

Requests:
- map status
- calculate quota_delta

Payments:
- normalize method names
- map statuses

---

#### Step 3. Load
Insert order (IMPORTANT):
1. plans (pre-created)
2. tokens
3. members (optional)
4. token_linked_accounts
5. token_usage_logs
6. payment_transactions

---

#### Step 4. Post-Processing
- rebuild daily_usage_counters
- validate quota consistency:
   initial_quota - usage = remaining_quota

---

#### Step 5. Validation Checks
Must verify:
- total tokens count match
- total usage count match
- random token audit:
   - quota correctness
   - linked accounts correctness

---

#### Step 6. Logging
Migration script must log:
- total migrated rows per table
- skipped records
- errors

### C.17.6 Migration Validation
After import:
- verify token counts
- verify quota values
- verify linked accounts
- verify sample request logs

### C.17.7 Rollback Strategy
If migration fails:
- restore VPS-1 system
- do not partially switch users

Rules:
- migration must be reversible
- never overwrite original data

### C.17.8 Migration Execution Plan
Steps:
1. Backup VPS-1
2. Setup VPS-2 (new system)
3. Run migration script
4. Validate data
5. Switch bot to new backend
6. Monitor system

### C.17.9 Migration Risks

#### C.17.9.1 Data Mismatch
- data mismatch between systems

#### C.17.9.2 Lost Quota
- lost quota or incorrect balances

#### C.17.9.3 User Confusion
- user confusion after migration

Mitigation:
- validation checks
- admin manual adjustment tools
- clear user messaging

#### C.17.9.4 Incorrect Plan Assignment
Description:
- wrong mapping may assign incorrect plan to tokens

Impact:
- unfair quota or limits

Mitigation:
- log all mappings
- allow admin review and correction

#### C.17.9.5 Incorrect Entitlement Conversion
Description:
- converting user-based subscription to quota-based token may miscalculate value

Impact:
- users receive too much or too little quota

Mitigation:
- log all conversions
- allow admin manual adjustment
- validate sample users before full migration

---

# =========================================================
# D. PHASES
# =========================================================

## D. Phases

### D.1 Foundation MVP
Target:
- plans
- tokens
- linked accounts
- quota logic
- core validation
- secure token handling

Modules:
- C.1
- C.2
- C.3
- C.5
- part of C.10

### D.2 Transfer and Recovery
Target:
- add account
- replace account
- lost device recovery
- transfer code flow

Modules:
- C.4
- part of C.11

### D.3 Payments and Activation
Target:
- Telegram Stars
- local manual payment
- OCR-assisted review
- admin approval flow

Modules:
- C.7
- part of C.9
- part of C.12

### D.4 Reporting and Audit
Target:
- admin history
- user history
- traceable logs
- operational visibility

Modules:
- C.6
- part of C.10
- part of C.11

### D.5 Language and UX Refinement
Target:
- Burmese-first UX
- English toggle
- multilingual content structure
- cleaner menus and messages

Modules:
- C.8
- part of C.11
- part of C.12

### D.6 Advanced Controls
Target:
- future anti-abuse
- advanced notifications
- family plan logic
- promotional flows
- analytics expansion

Modules:
- future queue promotions

### D.7 Legacy Discovery and Staging
Target:
- inspect legacy schema and logic
- classify data
- prepare PostgreSQL target mapping
- build staging import and cleanup flow

Modules:
- C.13
- part of C.10
- part of C.6

### D.8 Migration and Cutover
Target:
- import normalized data into PostgreSQL
- validate entitlement parity
- validate media delivery references
- switch traffic to the new environment
- maintain rollback-safe legacy read-only window

Modules:
- C.13
- part of C.2
- part of C.6
- part of C.9
- part of C.10

---

# =========================================================
# E. DEPENDENCIES
# =========================================================

## E. Dependencies

### E.1 Core Token Engine
Required before request enforcement, payments, and history.

### E.2 Linked Account Engine
Required before transfer/recovery and multi-account enforcement.

### E.3 Payment Review Workflow
Required before manual payment activation logic.

### E.4 Audit Logging Layer
Required before advanced admin reporting and dispute handling.

### E.5 Message Content Layer
Required before multilingual scaling and consistent UI text control.

### E.6 Legacy Data Backup Set
Required before migration work begins. Must include legacy SQLite DB, code snapshot, env/config snapshot, and service definitions.

### E.7 PostgreSQL Target Schema
Required before staging import, mapping validation, and constraint enforcement.

### E.8 Legacy-to-Target Mapping Rules
Required before member, payment, media, and analytics import logic can be finalized.

### E.9 Delivery Reference Validation
Required before cutover to confirm inherited Telegram source references remain usable on the new system.

### E.10 Backend API Layer
Required so the Telegram bot depends on backend APIs for:
- token validation
- quota checks
- linked-account checks
- usage logging
- payment state lookup

### E.11 WebApp Admin Layer
Required before authoritative member management, payment review, quota adjustment, and support operations can be considered complete.

### E.12 Atomic Entitlement Transaction Layer
Required before production release so quota deduction, daily counter update, and usage logging succeed or fail together. This prevents double deduction, partial writes, and quota drift under concurrent requests.

### E.13 Backend API Enforcement Layer
All business rules must be enforced via backend API.
Bot and WebApp must act as clients only.

Required before:
- production deployment
- multi-bot setup

### E.14 Unified WebApp Admin Portal
Required before production operations can fully move away from Telegram-admin-only workflows. The portal must cover token/member/payment/log/media management through backend APIs with audit-safe write paths.

---

# =========================================================
# F. RISKS
# =========================================================

## F. Risks

### F.1 Token Abuse Risk
Risk:
- token sharing beyond intended usage

Mitigation:
- linked-account slot limits
- logging
- revoke/reissue
- future anti-abuse controls

### F.2 OCR Reliability Risk
Risk:
- screenshot OCR may be inaccurate or manipulated

Mitigation:
- OCR as assistant only
- admin review
- review logs

### F.3 Scope Creep Risk
Risk:
- too many advanced features too early

Mitigation:
- phase-by-phase planning
- strict module boundaries
- queue-first approach

### F.4 Data Complexity Risk
Risk:
- poor schema causes reporting and workflow pain later

Mitigation:
- proper database planning
- traceable entities
- logging-first mindset

### F.5 Entitlement Carry-Over Risk
Risk:
- active members may lose time, quota continuity, or status accuracy during migration

Mitigation:
- recompute entitlement from authoritative dates
- preserve legacy references
- validate active user samples before cutover

### F.6 Delivery Reference Risk
Risk:
- inherited Telegram message references may fail on the new environment if channel access or message integrity differs

Mitigation:
- sample delivery validation
- fallback remediation queue
- do not decommission legacy infrastructure before parity confirmation

### F.7 Legacy Security Debt Risk
Risk:
- insecure legacy patterns may be copied into the new system

Mitigation:
- PostgreSQL target redesign
- hashed token storage
- foreign key enforcement
- secured admin exposure
- migration-specific security review

### F.8 Data Mapping Risk
Risk:
- weakly typed legacy SQLite fields and orphan rows may import incorrectly into normalized PostgreSQL structures

Mitigation:
- staging cleanup
- typed transformation rules
- rejection logging
- import audit tables

### F.9 Hardcoded Infrastructure Naming Risk
Risk:
- personal labels such as VPS-1 and VPS-2 may accidentally leak into code, config, or logic and reduce portability

Mitigation:
- enforce environment-based configuration
- use role-based architecture instead of personal server labels
- keep prompts and code deployment-agnostic

### F.10 Split Authority Risk
Risk:
- business state may become inconsistent if Telegram and WebApp both act as separate authorities

Mitigation:
- WebApp/backend as source of truth
- bot reads and enforces backend state only
- audit all admin-side modifications centrally

### F.11 Concurrent Quota Deduction Risk
Risk:
- simultaneous requests from linked accounts may cause double deduction, stale daily-cap checks, or mismatched remaining quota if updates are not atomic

Mitigation:
- transaction-based delivery commit
- row-level locking or equivalent safe concurrency control on token and daily counter rows
- duplicate guard key for short-window repeat requests
- append-only usage log before/with quota mutation trace

### F.12 Auto Replacement Confusion Risk
Description:
- users may not realize their account was replaced

Mitigation:
- clear notification message on replacement
- optional future: replacement history view in WebApp

### F.13 Delivery Payload Replay/Tamper Risk
Risk:
- users may reuse, forward, or tamper with delivery links/buttons to attempt unauthorized access

Mitigation:
- DB-stored short-lived delivery tokens
- backend verification before delivery
- telegram_user_id binding where applicable
- one-time-use enforced via DB record
- clear expiry handling and delivery-failure logging

### F.14 Admin Portal Overreach Risk
Risk:
- a powerful WebApp may accidentally bypass business rules or become a direct-database shortcut if implemented carelessly

Mitigation:
- all writes must go through backend service/API layer
- direct UI-to-database mutation must be avoided
- every mutation must create admin_action_logs and domain-specific logs where applicable
- destructive actions require explicit confirmation

### F.15 Button-State Mismatch Risk
Description:
- buttons shown do not match actual backend state

Examples:
- showing "Request File" when quota exhausted
- showing "Upgrade" when already highest plan

Impact:
- user confusion
- support load increase

Mitigation:
- backend must always validate state before generating buttons
- never rely on client-side assumptions
- centralize button decision logic

### F.16 State-to-UX Desynchronization Risk
Description:
- backend state does not match displayed message or buttons

Examples:
- quota exhausted but still shows request button
- token invalid but shows download button

Impact:
- user confusion
- incorrect actions
- support overhead

Mitigation:
- enforce centralized state → UX mapping
- do not allow direct message or button rendering outside mapping layer
- validate mapping coverage for all states

### F.17 Misconfiguration Risk (Admin Panel)
Description:
- incorrect admin changes can break system behavior

Examples:
- setting quota to zero
- removing all buttons from a critical flow
- invalid message templates

Impact:
- broken UX
- blocked users
- operational disruption

Mitigation:
- validation rules in WebApp
- fallback to default values
- audit logs for rollback
- optional confirmation for critical changes

### F.18 Inconsistent Admin Decisions
Description:
- different decisions for similar cases

Impact:
- unfair system behavior
- user dissatisfaction

Mitigation:
- follow defined playbook strictly
- standardize responses and actions

### F.19 Manual Override Abuse
Description:
- excessive manual quota restoration or approvals

Impact:
- revenue loss
- system imbalance

Mitigation:
- audit logs review
- limit admin actions where needed (future)

---

# =========================================================
# G. FUTURE ADDITIONS QUEUE
# =========================================================

## G. Future Additions Queue

### G.1 PIN or 2-Step Verification
Potential later enhancement for sensitive actions.

### G.2 Family Plan Logic
Potential later enhancement for higher-tier shared usage logic.

### G.3 Promotional Tokens
Potential later enhancement for campaigns or marketing offers.

### G.4 Category-Based Restrictions
Potential later enhancement for limiting certain content by plan.

### G.5 Analytics Dashboard
Potential later enhancement for usage, revenue, and operational insights.

### G.6 Advanced Anti-Abuse Scoring
Potential later enhancement for suspicious activity analysis.

### G.7 Migration Dry-Run Checker
Potential later enhancement for repeatable pre-cutover validation.

### G.8 Media Reference Health Scanner
Potential later enhancement for checking inherited Telegram delivery references at scale.

### G.9 Legacy Plan Retirement Workflow
Potential later enhancement for converting legacy carried-over users into fully native plan structures on renewal.

### G.10 Self-Service Migration Status Checks
Potential later enhancement for letting users check migration-related account status where appropriate.

### G.11 Post-Migration Analytics Parity Dashboard
Potential later enhancement for comparing old and new operational metrics after cutover.

---

# =========================================================
# H. PROMPT SOURCE AND IMPLEMENTATION FOCUS
# =========================================================

# =========================================================
# H.1 PROMPT SOURCE
# =========================================================

## H.1 Prompt Source

### H.1.1 Prompt Use Rule
This section exists so future prompts can be generated from the implementation plan without rewriting everything.

### H.1.2 Prompt Types to Generate Later
- VS Code implementation prompt by phase
- VS Code implementation prompt by module
- review/audit prompt
- database design prompt
- workflow prompt
- payment logic prompt
- UI/UX prompt
- bug-fix prompt
- refactor prompt

### H.1.3 Prompt Generation Rule
Always generate implementation prompts from the latest updated source sections, not from outdated memory.

### H.1.4 Prompt Environment Rule
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

### H.1.5 Migration Prompt Source Add
When generating migration or database prompts:
- treat legacy SQLite as source only
- target PostgreSQL for the new system
- preserve active member entitlements
- preserve payment and audit history where relevant
- validate inherited Telegram media delivery references
- normalize and clean legacy rows before production import

### H.1.6 Legacy Runtime Input Notes
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
# H.2 CURRENT IMPLEMENTATION FOCUS
# =========================================================

## H.2 Current Implementation Focus

- planning only
- PostgreSQL target schema
- legacy migration design
- WebApp-first member management architecture
- refine modules and phases first
- keep future build prompts consistent with this document

---

# =========================================================
# H.3 FINAL PLANNING NOTE
# =========================================================

## H.3 Final Planning Note

This document is the adjustable implementation blueprint for MovieVirus. It should be updated feature by feature, module by module, phase by phase, and section by section as the product definition becomes more mature.
