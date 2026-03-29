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

* Version: 1.1.0
* Last Updated: 2026-03-29
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

### A.3.24 | 2026-03-29

  * Locked final Phase-1 execution decisions for enforcement-sensitive logic
  * Confirmed daily cap scope as per token + Telegram account
  * Standardized daily reset at 00:00 Asia/Yangon (MMT, UTC+06:30)
  * Standardized duplicate protection window to 60 seconds
  * Confirmed linked-account overflow policy as deny new linking and direct user to admin
  * Reconfirmed no expiry for standard plans
  * Confirmed Telegram Stars auto activation
  * Confirmed admin quota restore is allowed with dedicated audit logging
  * Locked failed validation rule to 5 failed attempts -> 5 minute cooldown

### A.3.25 | 2026-03-29
  * Added strict decision-response contract for entitlement-related backend outcomes
  * Expanded state-to-UX mapping from message/button only into full status/message/button/quota/log contract
  * Standardized API response planning so bot and WebApp render backend-decided results only
  * Improved audit/debug consistency for validation, request, payment, and delivery flows

### A.3.26 | 2026-03-29
  * Cleaned structural inconsistencies caused by mixed or partially pasted updates
  * Removed outdated linked-account auto-replacement behavior from active implementation sections
  * Reconfirmed standard plans as quota-based and non-expiring by default
  * Standardized duplicate protection to 60 seconds and validation cooldown to 5 failed attempts -> 5 minute cooldown
  * Promoted multilingual bot content, buttons, menus, reminders, warnings, and notifications into WebApp-managed dynamic content
  * Added strict backend response-contract alignment for status_code, message_key, button_set_key, quota_effect, and log_type
  * Corrected section placement so content management is added under the real existing admin module structure

### A.3.27 | 2026-03-29
* Finalized Module 14 API contracts to match locked Phase-1 business rules
* Removed outdated auto-replacement behavior from access APIs
* Removed normal standard-plan expiry dependency from request/access APIs
* Standardized API responses around status_code, message_key, button_set_key, quota_effect, and log_type
* Aligned commit endpoints with post-delivery-only quota deduction and idempotent request handling
* Expanded admin and configuration endpoints to support dynamic content, linked-account reset, quota restore, and audit-safe recovery flows

### A.3.28 | 2026-03-29
- Resolved Phase-1 linked-account overflow contradiction in locked sections by standardizing deny-new-linking behavior
- Removed duplicated duplicate-protection text
- Removed duplicated content/localization screen section
- Reclassified C.10.6 as simplified schema overview instead of authoritative field-level schema
- Added folder-structure layering note to separate VPS/project-root layout from application-internal source layout

### A.3.29 | 2026-03-29
* Expanded WebApp-first control from content-only management into broader adjustable business and operational settings
* Clarified that plans, pricing, payment instructions, configurable reminders, button behavior metadata, and normal runtime settings should be WebApp-managed where safe
* Added explicit no-hardcode implementation preference for adjustable product settings
* Preserved code/environment ownership for secrets, infrastructure credentials, schema, and critical enforcement/security logic

### A.3.30 | 2026-03-29
* Synced implementation-plan display guidance with instruction-source cleanup
* Added Telegram Stars prices to default plan definitions for consistency with Phase-1 payment rules
* Added explicit behavioral-authority note so Module C.2 implementation ordering stays aligned with Document A

### A.3.31 | 2026-03-29
- Restored missing C.2.3 Fair Use Protection section
- Generalized C.14.10 Stars-payment rule to avoid stale response-field wording
- Corrected C.14.12 plan example so Premium Stars price matches default plan definitions

### A.3.32 | 2026-03-30
* Added change-safe architecture guidance for optional features, safe disablement, and future module extensibility
* Added portability guidance so backup, restore, packaging, and VPS migration remain routine operational paths
* Expanded admin configuration planning to include feature flags, module registry, and deployment/backup metadata
* Strengthened system-health, database-strategy, and project-structure rules for migration-safe and change-tolerant implementation

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

### A.5.2.0 File & Folder Structure Standardization (VPS + Codebase)

Purpose:
Ensure all MovieVirus deployments (VPS + codebase) follow a consistent, scalable, and maintainable structure to prevent disorder, debugging difficulty, and deployment risk.

Core Rules:

- Every component must have a predefined folder location.
- No random file placement in root or unrelated directories.
- Separate concerns clearly: bot logic, API, database, config, logs, scripts.
- Environment-specific files must be isolated (dev / staging / production ready).
- All paths must be predictable for automation and future scaling.

Layering note:
- This section defines the VPS/project-root deployment structure.
- The application source code inside `/movievirus/app/` must follow the internal code structure defined later in this document.
- Example interpretation:
  - VPS/project root layout: `/movievirus/app/`, `/bot/`, `/api/`, `/services/`, `/database/`, `/scripts/`
  - application-internal layout: source tree inside `/movievirus/app/`
- These are not competing structures; they are different layers of the same project.

---

#### A.5.2.1 Root Project Structure (Mandatory)

All VPS deployments must follow this base structure:

/movievirus/
├── app/                  # Core application logic
├── bot/                  # Telegram bot handlers & flows
├── api/                  # Internal or external API layer
├── services/             # Business logic services (quota, token, validation)
├── database/             # DB models, migrations, seeders
├── config/               # Environment configs (non-secret templates only)
├── scripts/              # Admin scripts, cron jobs, utilities
├── logs/                 # System logs (runtime, errors, audit exports)
├── storage/              # Temporary or persistent file storage
├── backups/              # DB backups and export snapshots
├── tests/                # Testing (future phase)
├── docs/                 # Local documentation (optional sync from master docs)
└── main_entry/           # Entry point (bot runner / app bootstrap)

Rules:
- No logic files allowed in root directory.
- Root should only contain folder structure + minimal bootstrap files.
- All modules must map into one of the above directories.

---

#### A.5.2.2 Module-Based Folder Mapping

Each major system module must live in a dedicated structure:

Example:

/services/token/
/services/quota/
/services/linked_accounts/
/services/payment/
/services/request/
/services/admin/

Rules:
- One module = one folder
- Each module must contain:
  - logic
  - validators
  - helpers (if needed)
- Avoid cross-module file scattering

---

#### A.5.2.3 Bot Structure Standardization

/bot/ must follow:

/bot/
├── handlers/        # Command and message handlers
├── flows/           # Step-by-step user flows (request, payment, etc.)
├── middlewares/     # Rate limit, validation, logging
├── keyboards/       # Telegram UI buttons
├── messages/        # Text templates (Burmese-first, EN optional)
└── routers/         # Routing logic

Rules:
- No business logic inside handlers (must call services/)
- Flows must be reusable and modular

---

#### A.5.2.4 Config & Secrets Handling

/config/
- config.template.json (or .env.example)
- NO secrets stored in repo or plain files

Rules:
- Real secrets must be injected via environment variables
- Separate:
  - system config
  - feature flags
  - environment configs

---

#### A.5.2.5 Logs & Audit Separation

/logs/
- app.log
- error.log
- security.log
- request.log

Rules:
- Logs must not mix with database records
- Critical actions must still be stored in DB (logs are not source of truth)

---

#### A.5.2.6 Script & Automation Rules

/scripts/
- backup.sh
- cleanup.sh
- migrate.sh
- deploy.sh

Rules:
- All manual VPS commands should be converted into reusable scripts
- Avoid undocumented one-time commands

---

#### A.5.2.7 Naming Conventions

- Use lowercase_with_underscores for folders
- Use clear module names (token_service, quota_service)
- Avoid abbreviations unless standard

---

#### A.5.2.8 Enforcement Rule

Any new feature, module, or implementation MUST:
- Declare its folder placement before coding
- Follow this structure strictly
- Be rejected/refactored if violating structure

---

Impact:

- Prevents messy VPS deployments
- Enables faster debugging and onboarding
- Supports scaling into multi-service architecture later
- Ensures consistency across future developers and automation tools

Dependencies:
- Applies to all modules (M01–Mxx)
- Required before Phase 2 expansion

Risks:
- RSK-NEW-01: Developers bypass structure → mitigated via enforcement rule
- RSK-NEW-02: Over-structuring early → mitigated by keeping Phase 1 minimal

Future Additions:
- Containerization (Docker structure alignment)
- Multi-instance deployment structure
- CI/CD pipeline directory alignment

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

### B.3.10 Locked Phase-1 Enforcement Decisions
The following decisions are locked for Phase 1 and must not be treated as implementation-time assumptions:

* daily cap scope = per token + Telegram account
* duplicate protection window = 60 seconds
* linked-account overflow behavior = deny new linking and direct user to contact admin
* replacement cooldown = not applicable in Phase 1
* standard plans = no time-based expiry
* Telegram Stars = auto activation after verified successful payment
* admin quota restore = allowed with dedicated audit logging

Purpose:
* convert planning logic into developer-safe implementation rules
* reduce ambiguity in DB schema, API contract, and workflow handling
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
- price: 3,000 MMK / 50 Stars
- total quota: 30
- daily cap: 3
- max linked accounts: 1

Basic:
- price: 5,000 MMK / 100 Stars
- total quota: 50
- daily cap: 5
- max linked accounts: 2

Plus:
- price: 10,000 MMK / 150 Stars
- total quota: 100
- daily cap: 10
- max linked accounts: 3

Pro:
- price: 15,000 MMK / 200 Stars
- total quota: 150
- daily cap: 15
- max linked accounts: 4

Premium:
- price: 20,000 MMK / 250 Stars
- total quota: 200
- daily cap: 20
- max linked accounts: 5

Notes:
- These are default presets only
- Admin can modify or create new plans dynamically
- Standard plans do not expire by time
- Optional expiry is reserved only for special-case plans, promos, or manual override scenarios
- Stars pricing is optional per plan and may be adjusted independently of MMK pricing through admin controls

### C.1.2 Token Statuses

Suggested statuses:

  * Active
  * Pending Activation
  * Expired (special plans only)
  * Suspended
  * Revoked
  * Exhausted

Rules:

  * standard quota-based plans should not rely on time-based expiry
  * Expired is reserved for special-case plans, promos, manual overrides, or explicitly configured time-based entitlements

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
     * IF linked: → use linked token → skip token input
     * ELSE: → request token → validate token → link account if slot available
  2. Enforce in exact order:
     * token existence
     * token status
     * total quota remaining
     * daily cap remaining
     * linked account eligibility
     * duplicate guard pre-check when relevant
  3. Linking rules:
     * auto-link if slot available
     * deny new linking if max linked accounts is already reached
     * return support-friendly linked-account/device-sharing-limit-reached response
  4. Standard plans must not depend on time-based expiry checks.
  5. Optional expiry checks are allowed only for explicitly configured special-case entitlements.
  6. Failed validation protection:
     * 5 failed attempts -> 5 minute cooldown

Purpose:

  * remove repeated token entry
  * enforce fairness via quota + daily cap + controlled sharing
  * keep backend logic deterministic
    
### C.2.2 Validation Rule

Check:

  * token existence
  * token status
  * total quota remaining
  * daily cap remaining
  * linked-account eligibility

Rules:

  * standard plans should not be denied by normal time-based expiry
  * daily cap reset boundary must use Asia/Yangon timezone
  * daily cap resets at 00:00 MMT (UTC+06:30)
  * failed validation cooldown = 5 failed attempts -> 5 minute cooldown

### C.2.3 Fair Use Protection
Rules:
- failed token validation must not deduct quota
- linked-account denial must not deduct quota
- file-not-found outcomes must not deduct quota
- duplicate-request suppression must not deduct quota
- delivery failure must not deduct quota
- quota deduction is allowed only after confirmed successful delivery and atomic commit

Purpose:
- preserve fairness for users
- reduce support disputes
- keep enforcement behavior aligned with commit-success-only deduction

### C.2.4 Backend Core Decision Engine

The backend must be the only authority for entitlement decisions.

Decision order per request:
  1. Resolve actor
     * identify telegram_user_id
     * identify whether access comes from linked-account path or token-input path
  2. Resolve entitlement
     * find token
     * reject if token missing
     * reject if status is not usable
  3. Resolve quota
     * reject if total_quota_remaining <= 0
     * reject if daily cap already reached for current date in Asia/Yangon timezone
  4. Resolve sharing rule
     * if user linked -> continue
     * if not linked:
       * link if slot available
       * else deny new linking
       * return linked-account limit reached response
       * do not change existing linked accounts
  5. Resolve validation-abuse protection
     * if failed-attempt cooldown is active -> deny with cooldown status
  6. Resolve duplicate guard
     * same token + same telegram_user_id + same file within safe window
     * return duplicate_ignored and do not deduct
  7. Resolve delivery attempt
     * create request record
     * issue delivery payload
     * on final success:
       * deduct quota
       * increment daily counter
       * log delivered event
     * on failure:
       * log failure
       * do not deduct
  8. Resolve post-commit reactions
     * quota reminder at 5 left
     * quota reminder at 1 left
     * exhausted action prompt at 0 left
     * user transparency history update
       
Behavioral alignment note:
- This implementation order must remain aligned with the behavioral enforcement order defined in the Master Instruction Source.
- When step granularity differs between the two documents, the Master Instruction Source is the behavioral authority and this section should be treated as implementation-level grouping of the same logic.

Purpose:

  * make the request engine predictable
  * keep all critical rules in one backend flow
  * reduce implementation drift across modules

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

### C.3.3 State → UX Mapping (Response Contract Binding)

All backend states must deterministically map to one stable decision contract.

This mapping must be centralized and consistent across all endpoints.

#### Core Mapping Structure

Each system state must define:

STATE:
  * internal backend state

OUTPUT:
  * status_code
  * message_key
  * button_set_key
  * quota_effect
  * log_type

Optional:
  * metadata

#### Mapping Table (Phase 1)

##### 1. ACCESS / TOKEN

STATE: token_required
  * status_code: TOKEN_REQUIRED
  * message_key: ASK_TOKEN
  * button_set_key: TOKEN_ENTRY
  * quota_effect: none
  * log_type: validation_prompt

STATE: token_invalid
  * status_code: INVALID_TOKEN
  * message_key: TOKEN_INVALID
  * button_set_key: TOKEN_RETRY
  * quota_effect: none
  * log_type: validation_denied

STATE: token_linked_success
  * status_code: TOKEN_LINKED_SUCCESS
  * message_key: TOKEN_LINKED_SUCCESS
  * button_set_key: MAIN_MENU
  * quota_effect: none
  * log_type: linked_account_added

##### 2. PLAN / ACCESS CONTROL

STATE: quota_exhausted
  * status_code: TOKEN_EXHAUSTED
  * message_key: QUOTA_EXCEEDED_WITH_ACTION
  * button_set_key: PLAN_ACTIONS
  * quota_effect: none
  * log_type: validation_denied

STATE: daily_limit_reached
  * status_code: TOKEN_DAILY_CAP_REACHED
  * message_key: DAILY_LIMIT_REACHED
  * button_set_key: PLAN_ACTIONS
  * quota_effect: none
  * log_type: validation_denied

STATE: linked_account_limit_reached
  * status_code: LINKED_ACCOUNT_LIMIT_REACHED
  * message_key: LINKED_ACCOUNT_LIMIT_REACHED
  * button_set_key: HELP
  * quota_effect: none
  * log_type: validation_denied

STATE: validation_cooldown_blocked
  * status_code: VALIDATION_COOLDOWN_BLOCKED
  * message_key: VALIDATION_COOLDOWN_BLOCKED
  * button_set_key: HELP
  * quota_effect: none
  * log_type: validation_blocked

##### 3. REMINDERS

STATE: quota_5_left
  * status_code: QUOTA_REMINDER_5_LEFT
  * message_key: REMINDER_5_LEFT
  * button_set_key: PLAN_ACTIONS
  * quota_effect: none
  * log_type: reminder_sent

STATE: quota_1_left
  * status_code: QUOTA_REMINDER_1_LEFT
  * message_key: REMINDER_1_LEFT
  * button_set_key: PLAN_ACTIONS
  * quota_effect: none
  * log_type: reminder_sent

STATE: quota_0_left
  * status_code: TOKEN_EXHAUSTED
  * message_key: REMINDER_0_LEFT
  * button_set_key: PLAN_PURCHASE
  * quota_effect: none
  * log_type: reminder_sent

##### 4. REQUEST FLOW

STATE: request_confirm
  * status_code: REQUEST_APPROVED
  * message_key: REQUEST_CONFIRM
  * button_set_key: REQUEST_CONFIRM
  * quota_effect: none
  * log_type: request_validated

STATE: request_processing
  * status_code: REQUEST_PROCESSING
  * message_key: REQUEST_PROCESSING
  * button_set_key: NONE
  * quota_effect: none
  * log_type: request_processing

STATE: duplicate_ignored
  * status_code: DUPLICATE_REQUEST_IGNORED
  * message_key: ERROR_RETRY
  * button_set_key: BACK
  * quota_effect: none
  * log_type: duplicate_ignored

##### 5. DELIVERY

STATE: delivery_success
  * status_code: REQUEST_COMMITTED
  * message_key: DOWNLOAD_BUTTON
  * button_set_key: DOWNLOAD_ACTION
  * quota_effect: decremented
  * log_type: delivery_success

STATE: delivery_failed
  * status_code: REQUEST_FAILURE_RECORDED
  * message_key: DELIVERY_FAILED
  * button_set_key: RETRY_ACTION
  * quota_effect: none
  * log_type: delivery_failed

##### 6. PAYMENT

STATE: payment_submitted
  * status_code: PAYMENT_SUBMITTED
  * message_key: PAYMENT_SUBMITTED
  * button_set_key: NONE
  * quota_effect: none
  * log_type: payment_submitted

STATE: payment_approved
  * status_code: PAYMENT_APPROVED_TOKEN_CREATED
  * message_key: PAYMENT_APPROVED
  * button_set_key: MAIN_MENU
  * quota_effect: none
  * log_type: payment_approved

STATE: payment_rejected
  * status_code: PAYMENT_REJECTED
  * message_key: PAYMENT_REJECTED
  * button_set_key: PLAN_PURCHASE
  * quota_effect: none
  * log_type: payment_rejected

#### Rules

  * every state MUST map to exactly one status_code
  * every state MUST map to exactly one message_key
  * every state MUST map to one button_set_key (or NONE)
  * every state MUST explicitly define quota_effect
  * every state MUST explicitly define log_type
  * no conditional entitlement UI logic should exist outside backend
  * frontend (bot) must only render what backend returns

Purpose:

  * eliminate UI inconsistency
  * ensure predictable behavior
  * standardize auditing and support interpretation
  * simplify debugging and future API expansion
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

### C.6.1 Admin Reporting

Enforcement Update:

  * max_linked_accounts must be strictly enforced
  * IF limit reached:
    * deny new account linking
    * provide clear error message
    * direct user to contact admin
  * linking does NOT consume quota

Admin should be able to inspect:

  * payment history
  * request history
  * file delivery history
  * linked-account history
  * account reset/recovery history
  * plan change history
  * quota adjustment history
  * suspicious activity history
  * admin action history

Linked Account Limit Rule:

  * when max_linked_accounts limit is reached:
    * system must deny new linking in Phase 1
    * no existing linked account should be auto-replaced
  * denial must:
    * create a traceable log entry
    * preserve current linked-account assignments
    * present a clear support-friendly message

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
  2. Bot calls: POST /request/validate

     Backend checks:
      * token existence
      * token status
      * quota
      * daily cap
      * linked account eligibility
      * failed-attempt cooldown
      * duplicate guard

     Response:
      * approved / denied
      * status_code
      * message_key
      * button_set_key
      * quota_effect
      * log_type

  3. IF approved:
      * backend creates request_id
      * quota_effect = none
      * bot proceeds to delivery

  4. Delivery bot sends file

  5. On success:
      * bot calls: POST /request/commit-success
      * backend:
        * verifies idempotency
        * deducts quota (once)
        * updates daily usage

  6. On failure:
      * bot calls: POST /request/commit-failure
      * backend:
        * logs failure
        * no quota deduction

Rules:

  * validation and approval must not deduct quota
  * only commit-success triggers deduction
  * commit-success must be idempotent
  * retries must not create additional deduction

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

Phase-1 delivery handoff note:
- The primary bot sends an inline button linking to the delivery bot.
- Recommended format: `t.me/{delivery_bot_username}?start={delivery_token}`
- The delivery bot receives the delivery token through `/start`, calls the backend delivery verification endpoint, and sends the file only if the token is valid and not already consumed.
- The primary bot does not send the file directly.

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

Locked Phase-1 duplicate window:

* duplicate protection window = 60 seconds

Recommended duplicate guard key inputs:

* token_id
* telegram_user_id
* file_id or normalized file identity
* normalized request context

Rules:

* same logical request inside 60 seconds should not deduct quota twice
* duplicate suppression must not replace hard request idempotency
* idempotency and duplicate window must both be enforced server-side


### C.7.8 Linked Account Limit Handling via API

When a new user links and the limit is reached:

Backend must:

  * deny new linking
  * preserve all existing linked accounts
  * write a traceable denial log
  * return linked-account limit reached response contract fields

Response should include:

  * status_code = LINKED_ACCOUNT_LIMIT_REACHED
  * message_key = LINKED_ACCOUNT_LIMIT_REACHED
  * button_set_key = HELP
  * quota_effect = none
  * log_type = validation_denied

Bot must:

  * show device-sharing / linked-account limit reached message
  * direct user to contact admin
  * not imply that any old account was replaced

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

### C.7.13 Validation Cooldown Rule

Add system setting:

  * validation_cooldown_seconds (default: 300)

Rules:

  * applies after repeated failed token validation attempts
  * locked Phase-1 rule = 5 failed attempts -> 5 minute cooldown
  * cooldown denial must not consume quota
  * cooldown denial must return clear user-facing message
  * cooldown events should be logged for audit and abuse review

---

# =========================================================
# C.8 MULTILINGUAL INTERFACE AND CONTENT LAYER
# =========================================================

## C.8 Module 08: Multilingual Interface and Content Layer

### C.8.1 Language Strategy
Prefer Burmese-first UI with English toggle.

### C.8.2 Content Storage Rule

Store all user-facing bot/UI content by stable content key with Burmese and English variants.

This includes:

  * bot messages
  * status messages
  * denial messages
  * menus
  * button labels
  * inline keyboard labels
  * reminders
  * notifications
  * warnings
  * payment instructions
  * request-flow prompts
  * help/support text

Rules:

  * visible text must not be hardcoded as the primary runtime source
  * backend/bot should reference stable keys and load display content dynamically
  * Burmese should remain the default language path
  * English should be supported through language preference / toggle
  * missing translations should fall back safely

### C.8.3 Dynamic Content Governance Rule

All bot-user visible content must be editable through the WebApp/admin content system without requiring code changes or redeployment for normal wording updates.

Scope:

  * bot menus
  * button labels
  * request prompts
  * payment instructions
  * warnings
  * reminders
  * notification text
  * success/failure explanations
  * support/help text

Rules:

  * code owns behavior and key selection
  * content system owns visible wording
  * business logic must not depend on exact visible sentence text
  * audit and status contracts must remain tied to stable codes/keys
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

Change-safe administration note:
- non-critical optional features should be introduced in a way that allows safe enable/disable control through backend-managed configuration where appropriate
- admin should be able to hide, disable, or defer incomplete non-core features without breaking entitlement, payment, delivery, or audit flows
- WebApp-controlled feature states must be validated server-side before activation

WebApp-first adjustment rule:
- Any setting that is expected to change during normal operation without requiring code logic redesign should be managed through WebApp-backed configuration or database records, not by editing scripts.
- This includes business-facing, admin-facing, and user-facing adjustable settings where safe.

Preferred WebApp-managed areas:
- plans and pricing
- quota and daily-cap values per plan
- linked-account limits per plan
- payment instructions and support text
- message templates and localization content
- menu labels and button labels
- button ordering and active/inactive state
- reminder thresholds and reminder enable/disable settings
- retry/cooldown/duplicate-window settings where explicitly allowed by system settings
- maintenance banners, notice text, and non-secret operational messaging

Not WebApp-managed:
- bot tokens
- API secrets
- database credentials
- cryptographic/hashing implementation details
- schema migrations
- low-level transaction logic
- core enforcement order
- security-critical hard fail rules that should not be casually edited

Purpose:
- reduce operational dependence on code edits
- make admin control practical for a non-programmer owner
- preserve backend integrity and security boundaries
  
### C.9.5 WebApp Admin System Scope
The WebApp admin system must be the primary operational control panel for MovieVirus.

Phase 1 WebApp scope:

  * dashboard overview
  * plan management
  * token management
  * member/user lookup
  * linked-account management
  * payment review and approval
  * quota adjustment
  * request history lookup
  * audit log review
  * media catalog management
  * content/localization management

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
  - plan_type

Additional WebApp-first rule:
- normal plan business adjustments must not require script edits
- pricing and quota behavior exposed at the plan-definition layer should be editable from WebApp
- plan presentation order and active/inactive state must be controllable from WebApp

Rules:
- plan edits must not silently rewrite historical token snapshots
- changes apply to future token creation unless explicit migration action is taken
- all plan mutations must create admin_action_logs

Purpose:
- keep plan administration manageable without code changes
- reduce support friction for pricing and packaging updates
- preserve historical auditability

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

Additional WebApp-manageable payment controls:
- edit visible payment instructions
- edit support/help text related to payment
- activate/deactivate non-secret payment-facing content entries where appropriate
- manage Telegram Stars price visibility where used through plan/config data
- manage local payment guidance text without redeploy

Rules:
- payment review actions must write payment_review_logs
- final approval/rejection must write admin_action_logs
- approved payment should generate or reveal send-ready token result through backend workflow
- payment-facing wording and instructions should not require script edits for normal updates
- secrets, private credentials, and infrastructure-only payment integrations must remain outside normal WebApp-editable content

Purpose:
- let admin maintain payment instructions without code changes
- reduce operational delay when payment guidance changes
- preserve audit and security boundaries


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

### C.9.16 Content and Localization Management Screen
Content / Localization screen must support:
* list content keys
* filter by category
* search by key
* edit Burmese content
* edit English content
* edit menu labels
* edit button labels
* edit notification/reminder text
* edit warning/denial text
* edit payment instruction text
* preview rendered content where practical
* activate/deactivate non-critical content entries where appropriate
* inspect content change history where available

Recommended categories:
* system_messages
* request_flow_messages
* payment_messages
* warning_messages
* reminder_messages
* notification_messages
* menu_labels
* button_labels
* help_and_support_messages

Rules:
* content editing must not bypass stable key usage
* content publishing must not require app redeploy for normal text changes
* critical enforcement outcomes must remain mapped to backend status codes and message keys
* content changes should be auditable
* this screen is the primary place for adjustable bot-facing wording and UX text
* visible wording should not be hardcoded in scripts when it can safely be resolved through content keys

Purpose:
* centralize UX wording control
* reduce hardcoded text debt
* support Burmese-first operation with English toggle
* allow faster support and product iteration
* make non-programmer administration practical

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

Final decision:

  * unified media model is used

Mapping:

  * movies → media_items (media_type = 'movie')
  * series → media_items (media_type = 'series')
  * episodes → episodes table

Purpose:

  * simplify search
  * enable unified indexing
  * support future content types
    
### C.10.5 Normalization Rule
Before import:
- recompute member status from dates instead of trusting legacy status blindly
- preserve original legacy IDs in mapping columns
- normalize CSV batch payloads into child rows
- clean orphan rows
- normalize enums and plan references
- enforce target-side foreign keys and indexes

### C.10.6 Final Phase-1 PostgreSQL Schema Blueprint
This section is a simplified Phase-1 schema overview only.

Authority rule:
* when any field, identity model, foreign key, uniqueness rule, index, or table responsibility conflicts with later detailed schema definitions in C.10, the later detailed schema definitions are authoritative
* this section must not be used as the sole implementation source for field-level database design

Locked structural note preserved from this overview:
* unified media model is used
* movies -> media_items (media_type = 'movie')
* series -> media_items (media_type = 'series')
* episodes -> episodes table
* file delivery references -> media_files

Purpose:
* provide a quick schema map for planning review
* preserve the unified media model decision
* defer all detailed implementation to the later detailed schema sections in C.10

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

field-level changes:
- add telegram_user_id (bigint, not null)
- change uniqueness to unique(token_id, telegram_user_id, usage_date)
- remove any older uniqueness rule of unique(token_id, usage_date)
- remove any older member-based uniqueness rule for Phase 1 quota enforcement

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
  * success
  * invalid_token
  * expired_special_plan
  * suspended
  * revoked
  * exhausted
  * linked_account_limit_reached
  * cooldown_blocked

Indexes:

  * index(matched_token_id, attempted_at desc)
  * index(telegram_user_id, attempted_at desc)
  * index(attempt_status, attempted_at desc)

Additional Rules:

  * after 5 failed token validation attempts, apply 5 minute cooldown
  * cooldown evaluation should use recent failed attempts for the same Telegram account and/or equivalent abuse-protection scope
  * linked-account-limit denial must be logged without changing existing linked accounts
  * normal standard plans should not produce expired validation status

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

#### Locked Daily Cap Scope

Daily cap must be tracked per:

  * token_id
  * telegram_user_id
  * usage_date

Implementation rule:

  * `daily_usage_counters` should represent one row per token, Telegram account, and system date
  * recommended uniqueness: unique(token_id, telegram_user_id, usage_date)
  * system date for daily reset must use Asia/Yangon timezone
  * reset boundary = 00:00 MMT (UTC+06:30)

Purpose:

  * enforce fair per-account daily limits under controlled sharing
  * align DB enforcement with the locked business rule
  * avoid timezone-related disputes

### C.10.11 Payment, Review, and Plan Change Tables

#### Locked Payment Activation Rule

Telegram Stars:

* verified successful Stars payments should auto-activate in Phase 1

Local manual payments:

* require admin approval in Phase 1
* OCR may assist but must not be sole approval authority

Rules:

* payment status transitions must be logged
* auto activation must still be idempotent
* one successful payment must not generate more than one token
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

### C.10.16 Button Configuration (WebApp-Controlled)

Buttons must support configuration via backend/WebApp as an active implementation requirement.

Rules:

  * button sets must be reusable
  * must be mapped to message_key or system state
  * labels must be loaded through content keys, not hardcoded text
  * WebApp should be able to control active/inactive state and order

#### Table: button_templates

Fields:

  * id
  * button_key
  * label_key
  * action_type
  * action_payload_template
  * sort_order
  * is_active
  * created_at
  * updated_at

Purpose:

  * allow admin to customize:
    * button labels
    * ordering
    * visibility
    * reusable action definitions

#### Button Set Logic (Runtime)

Backend should define button sets.

Examples:

  * HOME_MENU
  * SEARCH_RESULTS
  * PLAN_LIST
  * QUOTA_EXCEEDED
  * TOKEN_REQUIRED

Each set contains:

  * ordered list of button types

#### Example Button Set

QUOTA_EXCEEDED:

  * BUY_PLAN
  * VIEW_PLAN
  * HELP

Rules:

  * button sets must be reusable
  * must be mapped to message_key or system state
  * labels must be loaded through content keys, not hardcoded text
  * WebApp should be able to control active/inactive state and order

    
### C.10.17 Admin Configuration Data Model
System must support dynamic configuration and dynamic content management via WebApp.

Configuration ownership rule:
- Prefer database-backed, WebApp-managed configuration for any normal operational or business value that may need adjustment without changing core code.
- Do not hardcode adjustable business settings or normal UX content in scripts when a stable configuration model can own them safely.

Minimum dynamic configuration scope:
#### 1. message_templates
Purpose:
- store dynamic user-facing content
Examples:
- bot menus
- prompts
- warnings
- reminders
- payment instructions
- support/help text

#### 2. button_templates
Purpose:
- store reusable button definitions
Rules:
- labels must resolve through content keys, not hardcoded visible text
- active/inactive state should be manageable through WebApp where safe

#### 3. button_sets
Purpose:
- group reusable buttons for backend-selected UI states

#### 4. button_set_items
Purpose:
- control button ordering and set composition without script edits

#### 5. content_change_logs
Purpose:
- preserve content-specific audit history for wording and localization changes

#### 6. plan_definitions
Purpose:
- store admin-adjustable plan business values
Minimum fields:
- id
- plan_key
- name
- price_mmk
- price_stars
- total_quota
- daily_cap
- max_linked_accounts
- duration_days
- plan_type
- is_active
- updated_by
- updated_at

#### 7. system_settings
Purpose:
- store adjustable operational settings that are safe to manage without code edits
Minimum examples:
- duplicate_window_seconds
- max_delivery_retry
- validation_cooldown_seconds
- daily_reset_timezone
- quota_reminder_threshold_1
- quota_reminder_threshold_2
- maintenance_mode_enabled
- maintenance_notice_content_key
- telegram_stars_enabled
- local_payment_review_required

Examples:

  * duplicate_window_seconds = 60
  * max_delivery_retry = 3
  * validation_cooldown_seconds = 300
  * daily_reset_timezone = Asia/Yangon

#### 8. feature_flags
Purpose:
- allow safe enable/disable control for optional or future-facing features without code branching chaos

Minimum examples:
- enable_quota_reminders
- enable_stars_payment
- enable_manual_payment_submission
- enable_admin_content_preview
- enable_delivery_delete_after
- enable_beta_feature_x

Rules:
- feature flags must default to safe behavior
- disabling a non-critical feature must not break core entitlement flow
- feature flags must not be used to bypass locked core enforcement rules

#### 9. module_registry
Purpose:
- track whether a module is active, inactive, hidden, beta, or maintenance-disabled

Minimum examples:
- payment_manual_review
- reminders
- content_preview
- analytics_dashboard
- migration_tools

Rules:
- registry state must be runtime-readable by backend and WebApp
- inactive or hidden modules should fail gracefully with auditable reason codes

#### 10. deployment_snapshots
Purpose:
- record release/deployment metadata that helps rollback, migration, and environment verification

Minimum examples:
- release_label
- schema_version
- config_version
- deployed_at
- deployed_by
- environment_name

#### 11. backup_runs
Purpose:
- record backup execution history and verification results

Minimum examples:
- started_at
- completed_at
- backup_type
- storage_target
- verification_status
- initiated_by

#### 12. restore_runs
Purpose:
- record restore tests or real recovery operations for audit and disaster-recovery readiness

Minimum examples:
- started_at
- completed_at
- restore_target
- source_backup_id
- verification_status
- initiated_by

Additional rules:
- backup and restore history should be visible in admin audit/reporting tools
- export/import and migration readiness should be treated as normal system capability, not emergency-only work
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

### C.12.4 Dynamic Content Delivery Rule

All notifications and bot-visible messages must be rendered from stable content keys through the dynamic content system.

Rules:

  * backend should return status code / message_key / button_set rather than relying on hardcoded visible text
  * reminders, warnings, payment messages, and request-flow messages must follow the same system
  * multilingual rendering should occur at runtime using user language preference and safe fallback behavior
  * wording changes must not require bot redeploy for normal operational updates

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
- bot must not enforce quota, daily cap, linked-account, or payment state independently
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
  "code": "INVALID_TOKEN",
  "message": "Invalid token.",
  "data": null,
  "meta": {
    "request_id": "req_01H..."
  }
}
````

### C.14.2 Internal Client Authentication

Internal clients:

* primary Telegram bot
* delivery bot
* WebApp admin panel

Required headers:

* X-Service-Key: <server-side secret>
* X-Client-Type: primary_bot | delivery_bot | webapp
* X-Request-Id: <unique id>

Rules:

* service keys are server-side only
* user-facing Telegram clients must never see service keys
* admin login/session is separate from internal service authentication
* backend should reject requests with missing or invalid service key

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

* search movies/series before entitlement check
* allow discovery first, then require token/purchase at request stage

Query params:

* q = required string
* year = optional integer
* subtitle = optional string
* page = optional integer
* limit = optional integer

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

* fetch full details for one result before request

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

* used when requesting Telegram account is not yet linked
* validates plaintext token against backend
* links Telegram account only if a free linked-account slot exists
* denies linking when max linked accounts is already reached

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

Success example:

```json
{
  "success": true,
  "code": "TOKEN_VALIDATED_AND_LINKED",
  "message": "Token verified and Telegram account linked.",
  "data": {
    "decision": {
      "status_code": "TOKEN_VALIDATED_AND_LINKED",
      "message_key": "TOKEN_LINKED_SUCCESS",
      "button_set_key": "MAIN_MENU",
      "quota_effect": "none",
      "log_type": "linked_account_added",
      "metadata": {
        "token_id": "tok_01J...",
        "plan_code": "BASIC",
        "total_quota_remaining": 47,
        "daily_cap": 5,
        "daily_remaining": 5,
        "linked_account_action": "auto_linked"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Limit-reached example:

```json
{
  "success": false,
  "code": "LINKED_ACCOUNT_LIMIT_REACHED",
  "message": "Linked account limit reached.",
  "data": {
    "decision": {
      "status_code": "LINKED_ACCOUNT_LIMIT_REACHED",
      "message_key": "LINKED_ACCOUNT_LIMIT_REACHED",
      "button_set_key": "HELP",
      "quota_effect": "none",
      "log_type": "validation_denied",
      "metadata": {
        "linked_account_action": "denied_link_limit",
        "contact_admin_required": true
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Common denial codes:

* INVALID_TOKEN
* TOKEN_SUSPENDED
* TOKEN_REVOKED
* TOKEN_EXHAUSTED
* TOKEN_DAILY_CAP_REACHED
* LINKED_ACCOUNT_LIMIT_REACHED
* VALIDATION_COOLDOWN_BLOCKED

Rules:

* standard plans must not depend on normal expiry checks
* no oldest-account replacement in Phase 1
* denial must not consume quota

### C.14.5 Linked Account Validation API

POST /api/v1/access/validate-linked

Purpose:

* used for already-linked Telegram accounts
* should not require token input again unless link was reset or removed
* validates entitlement status before request continues

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
    "decision": {
      "status_code": "LINKED_ACCESS_OK",
      "message_key": "LINKED_ACCESS_OK",
      "button_set_key": "REQUEST_ACTIONS",
      "quota_effect": "none",
      "log_type": "validation_success",
      "metadata": {
        "token_id": "tok_01J...",
        "plan_code": "BASIC",
        "total_quota_remaining": 47,
        "daily_remaining": 5,
        "linked_account_action": "already_linked"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Common denial codes:

* LINK_NOT_FOUND
* TOKEN_SUSPENDED
* TOKEN_REVOKED
* TOKEN_EXHAUSTED
* TOKEN_DAILY_CAP_REACHED
* VALIDATION_COOLDOWN_BLOCKED

Rules:

* standard plans should not emit normal expiry denial
* endpoint must return backend decision object, not raw UI text

### C.14.6 Request Pre-Validation API

POST /api/v1/requests/validate

Purpose:

* validates whether a file request may proceed before delivery token is issued
* performs final entitlement checks before delivery starts
* does NOT deduct quota

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
    "decision": {
      "status_code": "REQUEST_APPROVED",
      "message_key": "REQUEST_CONFIRM",
      "button_set_key": "REQUEST_CONFIRM",
      "quota_effect": "none",
      "log_type": "request_validated",
      "metadata": {
        "request_id": "req_01J...",
        "token_id": "tok_01J...",
        "duplicate_guard_key": "dup_01J...",
        "total_quota_remaining": 47,
        "daily_remaining": 5,
        "delivery_token": "dlp_xxxxx",
        "delivery_expires_at": "2026-03-29T12:03:00Z"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Duplicate example:

```json
{
  "success": false,
  "code": "DUPLICATE_REQUEST_IGNORED",
  "message": "Same file was requested recently.",
  "data": {
    "decision": {
      "status_code": "DUPLICATE_REQUEST_IGNORED",
      "message_key": "ERROR_RETRY",
      "button_set_key": "BACK",
      "quota_effect": "none",
      "log_type": "duplicate_ignored",
      "metadata": {
        "duplicate_window_seconds": 60
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Common denial codes:

* LINK_NOT_FOUND
* TOKEN_SUSPENDED
* TOKEN_REVOKED
* TOKEN_EXHAUSTED
* TOKEN_DAILY_CAP_REACHED
* FILE_NOT_FOUND
* REQUEST_NOT_ALLOWED

Rules:

* validation and approval must not deduct quota
* duplicate requests within the safe window must not deduct quota
* duplicate protection must be enforced server-side

### C.14.7 Delivery Payload Verification API

POST /api/v1/delivery/verify-payload

Purpose:

* called by delivery bot before sending file
* validates DB-stored short-lived delivery token from primary bot
* ensures delivery request belongs to the intended Telegram user

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
    "decision": {
      "status_code": "DELIVERY_PAYLOAD_VALID",
      "message_key": "REQUEST_PROCESSING",
      "button_set_key": "NONE",
      "quota_effect": "none",
      "log_type": "delivery_verified",
      "metadata": {
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
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Denial codes:

* DELIVERY_PAYLOAD_INVALID
* DELIVERY_PAYLOAD_EXPIRED
* DELIVERY_PAYLOAD_ALREADY_USED
* DELIVERY_PAYLOAD_USER_MISMATCH

Rules:

* payload verification must not deduct quota
* payload expiry and one-time-use checks must be backend-enforced

### C.14.8 Request Commit Success API

POST /api/v1/requests/commit-success

Purpose:

* called only after delivery bot successfully sends the file
* deducts quota and updates daily counter atomically
* must be idempotent for the same request_id

Request:

```json
{
  "request_id": "req_01J...",
  "telegram_user_id": 123456789,
  "delivery_result": {
    "delivery_chat_id": 123456789,
    "delivery_message_id": 999001,
    "delivered_at": "2026-03-29T12:01:30Z"
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
    "decision": {
      "status_code": "REQUEST_COMMITTED",
      "message_key": "DOWNLOAD_BUTTON",
      "button_set_key": "DOWNLOAD_ACTION",
      "quota_effect": "decremented",
      "log_type": "delivery_success",
      "metadata": {
        "token_id": "tok_01J...",
        "quota_delta": 1,
        "total_quota_remaining": 46,
        "daily_remaining": 4
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Already-committed idempotent example:

```json
{
  "success": true,
  "code": "REQUEST_ALREADY_COMMITTED",
  "message": "Request was already committed earlier.",
  "data": {
    "decision": {
      "status_code": "REQUEST_COMMITTED",
      "message_key": "DOWNLOAD_BUTTON",
      "button_set_key": "DOWNLOAD_ACTION",
      "quota_effect": "none",
      "log_type": "delivery_success_existing",
      "metadata": {
        "request_id": "req_01J...",
        "idempotent_replay": true
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Denial codes:

* REQUEST_NOT_FOUND
* COMMIT_CONFLICT

Rules:

* only this endpoint may decrement quota
* same request_id must never decrement quota more than once
* validation must never decrement quota

### C.14.9 Request Commit Failure API

POST /api/v1/requests/commit-failure

Purpose:

* called when delivery fails after up to 3 retries
* records terminal delivery failure
* must not deduct quota
* should trigger admin notification workflow

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
    "decision": {
      "status_code": "REQUEST_FAILURE_RECORDED",
      "message_key": "DELIVERY_FAILED",
      "button_set_key": "RETRY_ACTION",
      "quota_effect": "none",
      "log_type": "delivery_failed",
      "metadata": {
        "admin_notification_queued": true,
        "quota_delta": 0
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Idempotency rule:

* if the same `request_id` / `request_key` is submitted again after failure was already recorded, backend must return the existing terminal result without creating another log row that could confuse reconciliation

### C.14.10 Telegram Stars Payment API

POST /api/v1/payments/telegram-stars/webhook

Purpose:

* receive confirmed Stars payment result
* auto-approve and generate token immediately in Phase 1

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
    "decision": {
      "status_code": "PAYMENT_APPROVED_TOKEN_CREATED",
      "message_key": "PAYMENT_APPROVED",
      "button_set_key": "MAIN_MENU",
      "quota_effect": "none",
      "log_type": "payment_approved",
      "metadata": {
        "payment_transaction_id": "pay_01J...",
        "token_id": "tok_01J...",
        "token_masked": "MV-****-****-1A6N",
        "plan_code": "BASIC"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

Rules:
* standard plans should not include normal expiry metadata in response
* plaintext token delivery should occur through the bot delivery flow, not be stored long-term

### C.14.11 Manual Payment API

POST /api/v1/payments/manual/submit

Purpose:

* submit local manual payment proof for admin review

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

Submit success example:

```json
{
  "success": true,
  "code": "PAYMENT_SUBMITTED",
  "message": "Payment submitted for review.",
  "data": {
    "decision": {
      "status_code": "PAYMENT_SUBMITTED",
      "message_key": "PAYMENT_SUBMITTED",
      "button_set_key": "NONE",
      "quota_effect": "none",
      "log_type": "payment_submitted",
      "metadata": {
        "payment_transaction_id": "pay_01J...",
        "payment_status": "pending_review"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

POST /api/v1/admin/payments/{payment_transaction_id}/approve

Purpose:

* admin approval for local manual payment
* generates token and returns/send-ready token details

Approve success example:

```json
{
  "success": true,
  "code": "PAYMENT_APPROVED_TOKEN_CREATED",
  "message": "Payment approved and token created.",
  "data": {
    "decision": {
      "status_code": "PAYMENT_APPROVED_TOKEN_CREATED",
      "message_key": "PAYMENT_APPROVED",
      "button_set_key": "MAIN_MENU",
      "quota_effect": "none",
      "log_type": "payment_approved",
      "metadata": {
        "payment_transaction_id": "pay_01J...",
        "token_id": "tok_01J...",
        "token_masked": "MV-****-****-1A6N",
        "plan_code": "PLUS",
        "delivery_action": "send_token_to_user"
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

POST /api/v1/admin/payments/{payment_transaction_id}/reject

Purpose:

* reject local manual payment with reason

Request:

```json
{
  "reason": "Screenshot does not match payment amount."
}
```

Reject success example:

```json
{
  "success": true,
  "code": "PAYMENT_REJECTED",
  "message": "Payment rejected.",
  "data": {
    "decision": {
      "status_code": "PAYMENT_REJECTED",
      "message_key": "PAYMENT_REJECTED",
      "button_set_key": "PLAN_PURCHASE",
      "quota_effect": "none",
      "log_type": "payment_rejected",
      "metadata": {
        "payment_transaction_id": "pay_01J..."
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
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
    "price_stars": 250,
    "total_quota": 200,
    "daily_cap": 20,
    "duration_days": null,
    "plan_type": "standard",
    "max_linked_accounts": 5,
    "is_active": true
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

POST /api/v1/admin/tokens/create
PATCH /api/v1/admin/tokens/{token_id}
POST /api/v1/admin/tokens/{token_id}/suspend
POST /api/v1/admin/tokens/{token_id}/reactivate
POST /api/v1/admin/tokens/{token_id}/revoke
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

Rules:

* `extend-expiry` should be reserved for special-plan-only admin cases if retained later
* standard-plan administration should focus on quota, status, linked accounts, and dynamic content control
* all mutation endpoints must create `admin_action_logs`

### C.14.13 Notifications and Status Message Contract

User-facing status codes that bot/UI should map clearly:

* TOKEN_REQUIRED
* INVALID_TOKEN
* TOKEN_VALIDATED_AND_LINKED
* LINKED_ACCESS_OK
* TOKEN_SUSPENDED
* TOKEN_REVOKED
* TOKEN_EXHAUSTED
* TOKEN_DAILY_CAP_REACHED
* LINKED_ACCOUNT_LIMIT_REACHED
* VALIDATION_COOLDOWN_BLOCKED
* DUPLICATE_REQUEST_IGNORED
* REQUEST_APPROVED
* REQUEST_COMMITTED
* REQUEST_FAILURE_RECORDED
* PAYMENT_SUBMITTED
* PAYMENT_APPROVED_TOKEN_CREATED
* PAYMENT_REJECTED

Optional special-plan-only status:

* TOKEN_EXPIRED

Rules:

* all denial reasons must be user-readable
* send-failure events should notify requester and admin
* final visible wording must come from `message_key` through the dynamic content system
* final visible actions must come from `button_set_key` through the button system
* normal standard plans should not emit expiry-based denial during normal operation
* bots and WebApp clients must not invent alternate status meaning outside backend contract

### C.14.14 API Idempotency and Logging Rules

Rules:

* all mutating endpoints should accept or generate a request correlation ID
* request commit endpoints must be idempotent to prevent double deduction
* duplicate request logic must be enforced server-side, not by bot memory
* all admin mutation endpoints must create `admin_action_logs`
* all verification failures should write `token_verification_attempt_logs` where relevant
* all delivery failures should write `token_usage_logs` or equivalent request/usage failure records with zero quota deduction
* all payment approval/rejection endpoints should create review/audit records
* all linked-account reset and quota-adjustment operations must be auditable

### C.14.15 Core Logic Response Rules

All entitlement-related endpoints must return backend-decided state, not UI guesses.

Validation, request, delivery, and payment endpoints should keep the standard API envelope while returning one strict decision object in `data.decision`.

Required decision fields:

* status_code
* message_key
* button_set_key
* quota_effect
* log_type
* metadata (optional)

Quota effect values:

* none
* decremented

Rules:

* standard plans should not emit expiry-based denial during normal operation
* quota and sharing state must drive primary UX
* message and button selection must be derived from backend response data
* quota_effect must be explicit so clients never guess whether quota changed
* log_type must be explicit so support/audit interpretation stays consistent
* metadata may enrich rendering and logging, but must not replace stable contract fields
* only commit-success may return `quota_effect = decremented`
* commit-success must be idempotent
* duplicate request logic must be enforced server-side, not by bot memory

State authority rule:

* only backend services may mutate token status, payment status, linked-account state, quota counters, approved-token linkage, and delivery-session state
* bots and WebApp clients must request backend decisions and render backend-decided results only

Recommended response shape:

```json
{
  "success": true,
  "code": "REQUEST_COMMITTED",
  "message": "Backend decision returned.",
  "data": {
    "decision": {
      "status_code": "REQUEST_COMMITTED",
      "message_key": "DOWNLOAD_BUTTON",
      "button_set_key": "DOWNLOAD_ACTION",
      "quota_effect": "decremented",
      "log_type": "delivery_success",
      "metadata": {
        "token_status": "active",
        "total_quota_remaining": 49,
        "daily_remaining": 4,
        "duplicate_flag": false,
        "linked_account_action": "already_linked",
        "reminder_trigger": null
      }
    }
  },
  "meta": {
    "request_id": "req_01H..."
  }
}
```

Standard denial priorities:

1. invalid token / link not found
2. unusable token status
3. total quota exhausted
4. daily cap reached
5. linked-account limit reached
6. validation cooldown blocked
7. duplicate ignored
8. delivery failure

### C.14.16 Button Set Definitions

Button sets must be predefined and reusable.
Each `button_set_key` maps to a list of button types.

Locked response requirements for Phase 1:

* `daily_remaining` must be computed for the current token + Telegram account pair
* `linked_account_action` must explicitly distinguish:

  * already_linked
  * auto_linked
  * denied_link_limit
* `duplicate_flag` must reflect the 60-second duplicate window result
* standard-plan responses must not imply normal expiry countdown
* admin-restored quota must appear as normal remaining quota in entitlement responses, while remaining separately auditable in admin/support views

---

#### Button Set List (Phase 1)

MAIN_MENU:

* SEARCH_MOVIE
* SEARCH_SERIES
* MY_PLAN
* BUY_PLAN
* HELP

PLAN_LIST:

* PLAN_STARTER
* PLAN_BASIC
* PLAN_PLUS
* PLAN_PRO
* PLAN_PREMIUM

PLAN_ACTIONS:

* BUY_PLAN
* UPGRADE_PLAN
* VIEW_PLAN

PLAN_PURCHASE:

* PLAN_LIST
* BACK

TOKEN_ENTRY:

* ENTER_TOKEN
* BUY_PLAN

TOKEN_RETRY:

* ENTER_TOKEN
* BACK

REQUEST_CONFIRM:

* CONFIRM_REQUEST
* CANCEL

DOWNLOAD_ACTION:

* DOWNLOAD_FILE
* BACK

RETRY_ACTION:

* RETRY
* CONTACT_SUPPORT

BACK:

* MAIN_MENU

NONE:

* (no buttons)

---

#### Rules

* button sets must be static keys, not dynamic arrays in logic
* backend selects `button_set_key` only
* bot resolves `button_set_key` into actual buttons

Purpose:

* reduce backend complexity
* standardize UX patterns
* enable WebApp-level customization later

### C.14.17 Admin Configuration Runtime Resolution

Backend must resolve configuration dynamically.

---

#### Message Resolution

IF message exists in DB (`message_templates`):
→ use DB version
ELSE:
→ fallback to default JSON

---

#### Button Resolution

1. backend returns `button_set_key`
2. system loads `button_sets` + `button_set_items`
3. system resolves:

   * button label (via `message_templates`)
   * action payload
4. bot renders final buttons

---

#### Plan Resolution

* backend must load `plan_definitions` dynamically
* no hardcoded plan logic allowed
* pricing, quota, sharing must come from DB

---

#### System Settings Resolution

* `system_settings` must control:

  * duplicate protection window
  * retry limits
  * validation cooldown
  * payment pending expiry
  * optional features
* backend must read settings at runtime or cache safely

---

#### Rules

* DB overrides always take priority over code defaults
* missing config must fallback safely
* invalid config must not crash system (fallback required)

Purpose:

* allow full control without redeploy
* support rapid iteration and fixes

```

## Summary

Affected documents: **B only**  
Affected sections: the full `C.14 Module 14: Backend API Contracts` block  
Changelog/version status: no new changelog entry is required just to correct this block unless you want to record this as a cleanup pass  
Clarification status: **resolved**
::contentReference[oaicite:1]{index=1}
```


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

Rules:
- every admin action must be attributable to one admin identity
- admin identity must map to `admin_users`
- no anonymous mutation of plans, tokens, payments, content, or settings

### C.15.2 Editable Areas
Admin must be able to control:

1. Messages
   - edit Burmese and English content
   - enable/disable messages
   - preview before publish

2. Buttons
   - change labels
   - reorder buttons
   - enable/disable buttons

3. Plans
   - create/edit plans
   - adjust price, quota, daily cap, sharing
   - activate/deactivate plan

4. System Settings
   - adjust duplicate window
   - adjust retry limits
   - adjust validation cooldown
   - toggle optional features

5. Tokens (Support Actions)
   - suspend token
   - reactivate token
   - revoke token
   - restore quota
   - reset linked accounts

Rules:
- visible text must not be hardcoded in bot logic
- all runtime content changes must resolve through DB-backed configuration
- standard plans should not rely on normal expiry controls
- special-plan-only expiry controls may exist later if explicitly enabled

### C.15.3 UI Requirements
WebApp must provide:
- dashboard overview
- message editor (with preview)
- plan editor (form-based)
- button configuration UI
- system settings panel
- token support action panel
- payment review queue
- audit log viewer
- member/user lookup
- linked-account inspection view
- request history view
- media library management screen

Example content update payload:
```json
{
  "message_key": "PAYMENT_REJECTED",
  "lang": "mm",
  "content": "ငွေပေးချေမှုကို အတည်ပြု၍ မရပါ။ ထပ်မံစစ်ဆေးပြီး ပြန်တင်ပါ။",
  "is_active": true
}
````

Example plan update payload:

```json
{
  "plan_key": "PLUS",
  "name": "Plus",
  "price_mmk": 10000,
  "price_stars": 1000,
  "total_quota": 100,
  "daily_cap": 10,
  "max_linked_accounts": 3,
  "plan_type": "standard",
  "duration_days": null,
  "is_active": true
}
```

### C.15.4 Safety Rules

* all changes must be logged in `admin_action_logs`
* critical changes must not overwrite silently
* confirmation step is recommended for high-impact changes
* before/after values must be stored for token state, quota restore, plan edits, linked-account reset, payment approval/rejection, and configuration edits
* DB-backed configuration must fail safely when invalid

Rules:

* no silent correction of quota, token state, or linked accounts
* no admin action should bypass audit logging
* admin-visible labels may change, but backend meaning must remain tied to stable keys and statuses

### C.15.5 Runtime Impact

* changes should apply immediately where safe
* no system restart required
* cached values must be refreshed periodically or invalidated
* content, button, and settings reads may use safe short-lived cache
* quota, token status, payments, linked accounts, and request state must always use authoritative backend/DB state

Purpose:

* empower admin to operate system without developer
* reduce downtime and dependency on code changes

### C.15.6 Admin Operation Playbook (Phase 1)

This defines how the system is operated daily and how common user issues are handled.

---

#### C.15.6.1 Daily Operations

##### C.15.6.1.1 Payment Review

Flow:

1. user submits payment
2. system marks transaction as `pending_review`
3. admin checks:

   * screenshot
   * OCR result (if available)
   * amount
   * payer reference
4. admin action:

   * approve → create token / activate entitlement
   * reject → store rejection reason
5. system records audit trail

Rules:

* always log approval source (`admin_manual`, `stars_auto`, or equivalent internal source classification)
* never activate plan without recorded transaction
* OCR must remain advisory only in Phase 1

Approve example:

```json
{
  "payment_transaction_id": "pay_01J...",
  "action": "approve",
  "reason": "Manual verification matched screenshot and amount."
}
```

Reject example:

```json
{
  "payment_transaction_id": "pay_01J...",
  "action": "reject",
  "reason": "Screenshot does not match expected amount."
}
```

##### C.15.6.1.2 User Support Handling

Admin must handle user issues through structured steps.

---

Case A: "Quota wrong"
Steps:

1. check usage logs
2. verify:

   * successful deliveries
   * duplicate protection result
   * commit-success record
3. IF system error confirmed:
   → restore quota manually
   → log action in `admin_action_logs`

Rules:

* quota restore must not overwrite request history
* quota restore must remain separately auditable from normal usage

Quota restore example:

```json
{
  "token_id": "tok_01J...",
  "delta_quota": 1,
  "reason_code": "manual_restore",
  "notes": "Duplicate charge correction after delivery failure review."
}
```

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

Rules:

* commit-failure must leave `quota_effect = none`
* repeated failure review should inspect request log, delivery log, and commit history together

---

Case C: "Token not working"
Steps:

1. verify token exists
2. check token state:

   * suspended
   * revoked
   * exhausted
3. IF linked account issue:
   → reset linked accounts OR explain linked-account limit reached behavior
4. IF validation cooldown active:
   → explain cooldown and expected retry timing

Rules:

* Phase 1 behavior is deny new linking when slots are full
* no auto-replace-oldest explanation should appear in support guidance

---

Case D: "Lost device"
Steps:

1. verify ownership (basic support confirmation)
2. reset linked accounts
3. allow re-linking from new Telegram account

Rules:

* linked account reset must NOT deduct quota
* must log reset action
* reset should preserve request and usage history

##### C.15.6.1.3 Plan & Payment Issues

Case E: "Payment made but not activated"
Steps:

1. find transaction
2. verify screenshot / OCR / payment details
3. IF valid:
   → approve manually
   → create token / activate plan
4. IF invalid:
   → reject with reason

---

Case F: "Upgrade request"
Steps:

1. confirm new payment
2. activate new plan immediately
3. old plan handling:

   * carry forward remaining quota
   * apply new plan quota
   * log plan change and delta

Rule:

* upgrade must apply immediately
* downgrade is not an in-place standard-plan operation

##### C.15.6.1.4 Content & Settings Operations

Case G: "Need to change wording"
Steps:

1. find `message_key`
2. edit Burmese and/or English content
3. preview
4. publish
5. verify bot renders updated content

Case H: "Need to change button order"
Steps:

1. load `button_set_key`
2. reorder button set items
3. save
4. verify expected rendering in bot

Case I: "Need to change duplicate window or cooldown"
Steps:

1. edit `system_settings`
2. save
3. verify runtime load / cache refresh
4. audit change

Rules:

* system meaning must remain stable even if wording changes
* invalid settings must not break runtime behavior

---

#### C.15.6.2 System Monitoring

Admin must periodically monitor:

* delivery failures
* repeated retry failures
* unusual token usage patterns
* payment anomalies
* repeated validation failures
* linked-account limit denials
* configuration errors or missing content keys

##### C.15.6.2.1 Delivery Monitoring

IF repeated delivery failures:
→ investigate:

* bot issues
* Telegram limits
* file availability
* expired or invalid delivery token flow
* commit-success / commit-failure inconsistencies

##### C.15.6.2.2 Abuse Monitoring

Signs:

* too many linked account changes
* rapid requests across multiple users
* repeated invalid token attempts
* unusual delivery-failure patterns
* suspicious payment submissions

Actions:

* suspend token
* review manually
* log support/admin action
* restore quota only when justified

---

#### C.15.6.3 Admin Actions (Allowed Operations)

Admin can:

* restore quota
* suspend token
* reactivate token
* revoke token
* reset linked accounts
* approve/reject payments
* modify plans
* adjust system settings
* edit dynamic content
* edit button configuration
* inspect logs and histories

Rules:

* all actions must be logged
* no silent changes allowed
* all actions should use auditable backend endpoints

Example admin audit row shape:

```json
{
  "admin_id": "adm_01J...",
  "action_type": "quota_restore",
  "target_type": "token",
  "target_id": "tok_01J...",
  "before_value": {
    "total_quota_remaining": 46
  },
  "after_value": {
    "total_quota_remaining": 47
  },
  "reason": "Delivery failure recovery",
  "created_at": "2026-03-29T12:15:00Z"
}
```
WebApp-first operations note:
- routine business and UX adjustments should be performed through WebApp-backed configuration and content records, not through script edits
- examples include plan updates, pricing updates, reminder settings, payment instruction changes, button visibility/order, and maintenance messaging
- security secrets, infrastructure credentials, and code-level enforcement logic remain outside normal WebApp administration

---

#### C.15.6.4 Communication Rules

All user-facing responses must:

* clearly explain reason for denial
* provide next action (buttons or guidance)
* avoid technical language
* render from backend `message_key` + `button_set_key`

Examples:

* quota exhausted → suggest plan purchase
* token invalid → guide to re-enter or purchase
* linked-account limit reached → guide user to contact admin
* validation cooldown → explain wait period simply

Purpose:

* reduce confusion
* reduce support load

---

#### C.15.6.5 Emergency Handling

Case J: System failure
Actions:

1. set system health to degraded or maintenance
2. pause affected features if needed
3. show safe user-facing message
4. investigate logs
5. restore service

---

Case K: Data inconsistency
Actions:

1. identify affected users/tokens
2. inspect request, usage, payment, and audit logs
3. correct data via admin tools
4. log all corrections

---

Rules:

* never silently ignore issues
* always maintain audit trace
* quota corrections and linked-account resets must remain visible in admin audit history

---

#### C.15.6.6 Audit & Traceability Rules

All admin actions must:

* be recorded in `admin_action_logs`
* include:

  * who performed action
  * what changed
  * before/after values
  * reason
  * timestamp

Purpose:

* accountability
* debugging support
* dispute resolution

### C.15.7 System Health State
System must support:
* normal
* degraded
* maintenance

Usage:
* bot changes behavior based on state
* admin dashboard displays status
* backend should fail closed for entitlement-sensitive operations when required state cannot be trusted

Change-safe behavior:
* non-critical module failure should prefer degraded mode over full system collapse where possible
* disabled optional features should return stable backend decisions instead of causing runtime crashes
* maintenance or disabled-module states should remain visible and auditable in admin tools

Purpose:
* graceful degradation
* clearer user messaging
* safer operation during partial outages, feature disablement, or staged rollout
### C.15.8 Database Access Strategy
Use:
* Knex for queries/migrations
* raw SQL for critical transactions

Avoid:
* relying solely on ORM abstractions for atomic quota deduction, commit handling, or concurrency-sensitive operations

Rules:
* request commit-success should be a DB transaction
* quota decrement + usage log + daily counter update must succeed or roll back together
* audit-critical writes should not be fire-and-forget
* schema changes should prefer additive, backward-compatible rollout where practical
* optional feature data structures should not destabilize core entitlement tables
* migration/export/import workflows should be supportable without redesigning database ownership boundaries

Purpose:
* preserve correctness
* reduce migration risk
* support safer iteration and VPS portability

### C.15.9 Admin Auth Security

Add:

* session timeout (30–60 min)
* login attempt limit
* IP logging
* CSRF protection if session/cookie-based
* secure password hashing
* audit log on login/logout and failed admin login attempts

Rules:

* admin session must be separate from service-key auth
* service keys are for internal clients only
* single-admin Phase 1 still requires auditable identity

````

---


# =========================================================
# C.16 BACKEND IMPLEMENTATION BLUEPRINT (NODE.JS)
# =========================================================

## C.16 Module 16: Backend Implementation Blueprint (Node.js)

### C.16.1 Tech Stack
- Runtime: Node.js (LTS)
- Framework: Express.js (or Fastify optional)
- Database: PostgreSQL
- Query Layer: Knex + raw SQL for critical paths
- Auth: Service key (internal), session (admin)
- Deployment: VPS (legacy → new migration ready)

Rules:
- backend must remain the only authority for quota, token state, linked accounts, and payment state
- standard-plan enforcement must not depend on normal expiry logic
- dynamic content, button sets, plans, and settings must be DB-backed and runtime-resolved

### C.16.2 Project Structure
Recommended structure:

```text
/movievirus/
  /app
    /api
      /routes
      /controllers
      /schemas
      /services
        /auth
        /token
        /quota
        /linked_accounts
        /request
        /delivery
        /payment
        /admin
        /search
        /content
        /config_runtime
        /feature_flags
        /module_registry
        /backup_restore
    /database
      /migrations
      /seeds
      /queries
    /bot
      /handlers
      /flows
      /middlewares
      /keyboards
      /messages
      /routers
    /config
    /scripts
    /logs
    /storage
    /backups
    /exports
    /imports
    /tests
  main_entry/
````

Rules:

* no business logic inside bot handlers
* controllers should remain thin
* services own business logic
* critical transactional SQL may bypass helper abstraction where clarity and atomicity matter more

### C.16.3 Module Responsibilities

#### auth

* service key validation
* request authentication
* admin session auth
* request identity / correlation handling

#### token

* token validation
* linking logic
* token state handling
* masked token handling
* secure hash comparison

#### quota

* total quota checks
* daily cap checks
* atomic quota decrement
* manual quota restore support

#### linked_accounts

* linked-account lookup
* auto-link when allowed
* deny link when max linked accounts reached
* reset specific/all linked accounts via admin

#### request

* request validation
* duplicate protection
* request lifecycle state handling
* commit success/failure handling

#### delivery

* delivery token creation
* delivery payload verification
* one-time use enforcement
* delivery window / delete-after metadata

#### payment

* Telegram Stars webhook
* manual payment handling
* OCR-assisted review support
* payment approval/rejection flows
* token creation after approved payment

#### admin

* plan management
* token management
* quota restore
* linked-account reset
* audit log access
* system settings updates

#### search

* file search + metadata
* details lookup
* unified media search result composition

#### content

* dynamic message resolution
* button set resolution
* fallback behavior
* content preview support

#### config_runtime

* system settings resolution
* safe caching / invalidation
* duplicate window / cooldown / retry limit loading

### C.16.4 Controller → Service Flow

Example:
POST /api/v1/requests/validate

Flow:

* `requests.controller.validateRequest`
* `auth.service.assertInternalClient`
* `linked_accounts.service.resolveLinkedUser`
* `token.service.assertUsableToken`
* `quota.service.assertQuotaAvailable`
* `quota.service.assertDailyCapAvailable`
* `request.service.checkDuplicateWindow`
* `delivery.service.issueDeliveryToken`
* `response.service.buildDecision`

Example decision response:

```json
{
  "success": true,
  "code": "REQUEST_APPROVED",
  "message": "Request approved.",
  "data": {
    "decision": {
      "status_code": "REQUEST_APPROVED",
      "message_key": "REQUEST_CONFIRM",
      "button_set_key": "REQUEST_CONFIRM",
      "quota_effect": "none",
      "log_type": "request_validated",
      "metadata": {
        "request_id": "req_01J...",
        "duplicate_window_seconds": 60,
        "daily_remaining": 5
      }
    }
  },
  "meta": {
    "request_id": "req_01J..."
  }
}
```

### C.16.5 Critical Transaction Logic

Commit success must be atomic.

Within single DB transaction:

1. confirm request exists and is not already committed
2. insert usage log
3. decrement token quota
4. update daily usage counter
5. mark request as committed
6. return updated quota state

If any step fails:

* rollback entire transaction

Pseudo-SQL shape:

```sql
BEGIN;

SELECT id, token_id, member_id, is_committed
FROM request_logs
WHERE request_id = :request_id
FOR UPDATE;

-- fail if already committed or invalid state

INSERT INTO usage_logs (
  token_id,
  member_id,
  request_id,
  media_item_id,
  quota_used,
  created_at
) VALUES (
  :token_id,
  :member_id,
  :request_id,
  :media_item_id,
  1,
  NOW()
);

UPDATE tokens
SET total_quota_remaining = total_quota_remaining - 1,
    updated_at = NOW()
WHERE id = :token_id
  AND total_quota_remaining > 0;

INSERT INTO daily_usage (
  token_id,
  member_id,
  usage_date,
  request_count
) VALUES (
  :token_id,
  :member_id,
  :usage_date,
  1
)
ON CONFLICT (token_id, member_id, usage_date)
DO UPDATE SET request_count = daily_usage.request_count + 1;

UPDATE request_logs
SET is_committed = TRUE,
    status = 'success',
    updated_at = NOW()
WHERE request_id = :request_id;

COMMIT;
```

Rules:

* only commit-success may deduct quota
* validation must never deduct quota
* duplicate-safe and idempotent behavior must be enforced server-side

### C.16.6 Middleware Layer

Required middleware:

* `serviceAuthMiddleware`
* `adminSessionMiddleware`
* `requestLoggerMiddleware`
* `errorHandlerMiddleware`
* `rateLimiterMiddleware`
* `validationMiddleware` (schema-based)
* `requestIdMiddleware`

Rules:

* every request should have a correlation/request ID
* admin auth and service-key auth must remain separate
* validation failures should map to stable error codes where possible

### C.16.7 Delivery Payload System

Use DB-stored delivery token.

Store:

* request_id
* token_id
* telegram_user_id
* expiry timestamp
* is_used
* created_at

Rules:

* short-lived (≤ 3 minutes)
* validated by backend before delivery
* one-time use enforced via DB record
* delivery verification must not deduct quota

Example delivery token row:

```json
{
  "delivery_token": "dlp_xxxxx",
  "request_id": "req_01J...",
  "token_id": "tok_01J...",
  "telegram_user_id": 123456789,
  "expires_at": "2026-03-29T12:03:00Z",
  "is_used": false
}
```

### C.16.8 Retry & Job Handling

* retry delivery up to 3 times
* use simple retry loop in Phase 1
* queue system is optional future work

Admin notification trigger:

* delivery failure after max retries
* abnormal internal error
* repeated verification failures
* payment review backlog thresholds (optional later)

Retry flow example:

```json
{
  "request_id": "req_01J...",
  "retry_count": 3,
  "final_status": "failed",
  "quota_effect": "none",
  "admin_notification_queued": true
}
```

### C.16.9 Logging Strategy

Log types:

* request logs
* token verification logs
* payment logs
* admin logs
* error logs
* delivery logs
* configuration change logs

Rules:

* do not overwrite logs
* append-only for audit-critical logs
* request_logs and usage_logs must remain reconcilable
* admin_action_logs must store before/after when meaningful

### C.16.10 Environment Config

Example `.env` structure:

```dotenv
APP_ENV=production
PORT=3000
DATABASE_URL=postgres://user:pass@localhost:5432/movievirus
SERVICE_KEY_PRIMARY_BOT=svc_primary_xxxxx
SERVICE_KEY_DELIVERY_BOT=svc_delivery_xxxxx
SERVICE_KEY_WEBAPP=svc_webapp_xxxxx
TOKEN_HASH_SECRET=tok_hash_xxxxx
SESSION_SECRET=sess_xxxxx
TELEGRAM_PRIMARY_BOT_TOKEN=123:abc
TELEGRAM_DELIVERY_BOT_TOKEN=456:def
LOG_LEVEL=info
```

Rules:

* do not store live secrets in repo
* real runtime secrets must be environment-injected
* service keys must never be exposed to user clients
* no `DELIVERY_TOKEN_SECRET` is required if delivery tokens are DB-stored opaque tokens rather than signed payloads

### C.16.11 Phase 1 Build Order

1. setup project + DB connection
2. implement internal auth middleware
3. implement token validation + linked-account module
4. implement quota + daily cap enforcement
5. implement request validation
6. implement commit success logic
7. implement delivery payload system
8. implement search endpoints
9. implement payment endpoints
10. implement admin endpoints
11. implement dynamic content + button resolution
12. add logging + error handling
13. add admin WebApp operational screens

### C.16.12 Phase 1 Constraints

* single server (no microservices)
* no queue system required initially
* no Redis caching required initially
* keep logic centralized
* avoid overengineering
* prioritize correctness in entitlement and audit paths over premature optimization

### C.16.13 Future Expansion Ready

* queue system (BullMQ)
* Redis caching
* multi-instance scaling
* load balancer
* analytics dashboard
* advanced admin role/permission model
* event-driven notifications
* richer observability pipeline

````

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
- migration must preserve where possible:
  - tokens or equivalent entitlement identity
  - user associations
  - quota correctness
  - payment records
  - media references
  - audit-relevant history

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
- migration must convert user subscription → token entitlement
- one legacy user normally becomes:
  - one member
  - one token
  - one linked account

Rules:
- do NOT directly copy legacy `plan_id` logic into new quota-based entitlement
- do NOT directly preserve legacy expiry as a standard-plan requirement
- standard migrated plans should become quota-based and non-expiring unless explicitly flagged as special-case carryover plans

### C.17.2 VPS-1 Backup Requirements
Before any implementation or cutover:

Create full backup of VPS-1:
1. database dump
   - full SQL dump
   - include all tables
2. file storage / references
   - media references
   - metadata
3. bot configuration
   - environment variables
   - tokens / secrets / deployment notes

Rules:
- store backup securely
- keep at least 2 copies
- do not overwrite original
- backup must be read-only preserved during migration validation window

### C.17.3 Old System Data Analysis
Identify:
- tables and structure
- legacy token format or subscription identifiers
- user linkage model
- request logs
- payment records
- media reference model
- delivery reference dependencies

Output:
- data inventory document
- mapping notes
- integrity issues list
- discard / preserve list

### C.17.4 Data Mapping Strategy (Revised Based on VPS-1)
Migration must transform user-based system into token-based system.

---

#### C.17.4.1 Users → Members + Tokens + Linked Accounts
Legacy:
- users table contains subscription info

New:
For each active legacy user:
- create one `members` row
- create one `tokens` row
- create one `linked_accounts` row
- connect linked account to member + token

Default Phase 1 migration rule:
- 1 legacy user = 1 token
- 1 legacy user = 1 linked account

Rule:
- future merging/sharing can be handled manually after migration if needed
- migration should prioritize correctness and simplicity, not automatic family/share reconstruction

---

#### C.17.4.2 Plan Conversion
Legacy:
- plan_id + expiry_date
- daily usage only
- no total quota

New:
- total quota required
- daily cap required
- max linked accounts required

Conversion strategy:

Option A (recommended):
- derive remaining quota based on remaining entitlement value using remaining days × daily limit

Example:
- 10 days left × 3/day → 30 quota remaining

Option B:
- fixed mapping per plan based on business-defined conversion table

Rules:
- all conversions must be logged
- conversion policy must be consistent across all migrated users
- migrated standard entitlements should become quota-based and non-expiring
- only explicitly chosen special carryover cases may retain expiry semantics

Conversion log example:
```json
{
  "legacy_user_id": 1001,
  "legacy_plan_id": "plan_basic",
  "remaining_days": 10,
  "legacy_daily_limit": 3,
  "derived_total_quota_remaining": 30,
  "assigned_plan_key": "STARTER",
  "plan_type": "standard",
  "notes": "Converted from legacy expiry-based entitlement to quota-based token."
}
````

---

#### C.17.4.3 Daily Usage → Usage Logs / Daily Usage

Legacy:

* daily_usage may be aggregated

New:

* `usage_logs` is event-based
* `daily_usage` is counter-based

Strategy:

* exact historical replay may not be reconstructable
* priority = correct remaining quota and safe current counters

Options:

* reconstruct minimal synthetic usage rows if reliable enough
* OR initialize remaining quota only and begin new event logging from cutover date

Rule:

* prioritize quota correctness over perfect historic replay
* avoid inventing unreliable detailed history

---

#### C.17.4.4 Delivery Tokens → DISCARD

Legacy:

* delivery tokens are temporary access tokens

New:

* delivery tokens are runtime-only and DB-stored short-lived records

Rule:

* DO NOT migrate legacy delivery tokens as active records
* expired / used short-lived access records should not become new entitlement records

---

#### C.17.4.5 Requests / Events

Legacy:

* request_events + requests

New:

* `request_logs` + `usage_logs`

Strategy:

* optional detailed migration
* preserve request history where operationally useful
* successful request rows may be migrated if they improve audit/support value
* failed request history may be selectively migrated if reliable

Rule:

* migrated failed requests must not imply quota deduction
* migrated historical request detail should not distort current remaining quota

---

#### C.17.4.6 Payments

Legacy:

* transactions table or equivalent

New:

* `payments`

Rule:

* migrate all completed/relevant payments
* preserve:

  * amount
  * method
  * approval metadata
  * payment timestamps
  * review notes where available

If token linkage is uncertain:

* preserve as historical payment row with nullable or indirect token relation

---

#### C.17.4.7 Media Tables

Legacy:

* movies
* series
* series_episode_map
* file/message reference tables

New:

* `media_items`
* `episodes`
* `media_files`

Rule:

* MUST migrate operational media references
* preserve:

  * file_chat_id
  * file_message_id
  * file_unique_id if available
  * quality / language / source metadata where useful

Mapping:

* movies → `media_items` (`media_type = 'movie'`)
* series → `media_items` (`media_type = 'series'`)
* episode mappings → `episodes`
* file/message references → `media_files`

---

#### C.17.4.8 Discard Tables

Do NOT migrate as active new-system entities:

* delivery_tokens
* message_delete_queue
* expiry_reminders (unless retained only as archive)
* ai_events (optional analytics only)
* search_miss (optional analytics only)
* stale transient job/queue tables

Rule:

* discard operational noise
* preserve only what supports entitlement correctness, delivery continuity, payment traceability, or audit value

---

#### C.17.4.9 Integrity Fixes During Migration

Must fix:

* orphan records
* expired-but-active legacy users
* inconsistent status
* duplicate Telegram user bindings
* invalid payment state combinations
* missing media reference pairs where recoverable

Rule:

* migration must clean data, not copy errors
* questionable rows should be quarantined for admin review rather than silently imported

### C.17.4.10 Detailed Table Mapping (Old → New)

Mapping must be defined at table and field level.

#### 1. Tokens / Entitlements

Old → New:

* legacy subscription identity / token field → `tokens.token_hash` (hash during migration)
* legacy created_at → `tokens.created_at`
* legacy quota/derived entitlement value → `tokens.total_quota_remaining`
* derived plan mapping → `tokens.plan_id`
* derived status → `tokens.status`

Rules:

* generate masked token preview if token string exists and is migrated as entitlement identity
* if old system has no reusable token, generate new secure token and preserve legacy reference in migration notes
* do not store plaintext token long-term

Additional:

* `tokens.total_quota` may be set from mapped plan total or derived starting quota policy
* `tokens.plan_type` behavior should treat standard migrated plans as non-expiring unless flagged otherwise

---

#### 2. Users → Members / Linked Accounts

Old → New:

* old_users.telegram_user_id → `members.telegram_user_id`
* old_users.username → `members.username`
* old_users.first_name / last_name → `members.first_name` / `members.last_name`
* member identity → `linked_accounts.member_id`

Rules:

* each migrated active user should normally receive one linked account row
* assign `linked_accounts.linked_at` using earliest reliable user-created or subscription-created time
* preserve only valid Telegram identity data

---

#### 3. Requests → Request Logs / Usage Logs

Old → New:

* old_requests.user_id or telegram_user_id → `members.id` / linked member resolution
* old_requests.entitlement_ref → `tokens.id`
* old_requests.file_id / media reference → `request_logs.media_item_id`
* old_requests.status → `request_logs.status`
* old_requests.created_at → `request_logs.created_at`

Rules:

* only historically successful requests should imply quota usage
* if migrated into `usage_logs`, failed requests must have no quota deduction
* request history may be selectively migrated if confidence is high

---

#### 4. Payments

Old → New:

* old_payments.amount → `payments.amount`
* old_payments.method → `payments.method`
* old_payments.status → `payments.status`
* old_payments.timestamp → `payments.created_at`
* old review metadata → review notes / audit support fields

Rules:

* map statuses carefully
* preserve historical truth even when old labels differ
* keep rejected / pending records when useful for support history

---

#### 5. Derived / Missing Fields

Fields not present in old system must be generated:

* secure token value or token hash
* token masked preview
* `daily_usage` counters from cutover onward
* migration notes / mapping logs
* `admin_action_logs` rows for manual corrections after migration

Rule:

* generated fields must be deterministic or clearly logged as generated

### C.17.4.11 Plan Assignment Logic

Old system may not have structured quota plans.

Rules to assign plan_id:

Option A (recommended):

* map based on derived remaining quota:

  * ≤30 → Starter
  * ≤50 → Basic
  * ≤100 → Plus
  * ≤150 → Pro
  * > 150 → Premium

Option B:

* map based on payment amount

Fallback:

* assign default plan and log for admin review

All mappings must be logged for audit.

### C.17.5 Migration Script

Implementation:

* create one-time migration script
* read old DB
* transform data
* insert into new DB

Rules:

* do not bypass target integrity rules without logging why
* preserve audit integrity
* log all migration actions
* support dry-run mode before real import

### C.17.5.1 Migration Execution Logic

Migration must run in controlled stages.

---

#### Step 1. Extract

* read old database
* export tables:

  * subscriptions / tokens / equivalent entitlement source
  * users
  * requests
  * payments
  * media tables

---

#### Step 2. Transform

For each dataset:

Entitlements:

* hash token if reusable token exists
* or generate new secure token
* assign plan_id
* compute derived quota
* compute status

Users:

* normalize Telegram identity
* deduplicate `telegram_user_id`

Requests:

* map status
* identify which rows affect quota history

Payments:

* normalize method names
* map statuses

Media:

* unify into `media_items`, `episodes`, `media_files`

---

#### Step 3. Load

Insert order (IMPORTANT):

1. plans (pre-created)
2. admin_users (if seeded)
3. members
4. tokens
5. linked_accounts
6. media_items
7. episodes
8. media_files
9. request_logs (optional / selective)
10. usage_logs (optional / selective)
11. daily_usage (if initialized)
12. payments

---

#### Step 4. Post-Processing

* rebuild daily usage where needed
* validate quota consistency:

  * starting quota - committed usage = remaining quota
* validate one linked account per migrated default token unless explicitly adjusted

---

#### Step 5. Validation Checks

Must verify:

* total migrated active users count
* total tokens count
* quota correctness samples
* linked account correctness samples
* payment row counts
* media reference integrity samples

---

#### Step 6. Logging

Migration script must log:

* total migrated rows per table
* skipped records
* quarantined records
* generated tokens count
* errors
* manual review required list

Migration report example:

```json
{
  "members_migrated": 198,
  "tokens_created": 198,
  "linked_accounts_created": 198,
  "payments_migrated": 176,
  "media_items_migrated": 12450,
  "episodes_migrated": 8420,
  "media_files_migrated": 20870,
  "quarantined_records": 7,
  "errors": 0
}
```

### C.17.6 Migration Validation

After import:

* verify token counts
* verify quota values
* verify linked accounts
* verify sample request logs
* verify payment history samples
* verify media reference playback/delivery for sampled items

### C.17.7 Rollback Strategy

If migration fails:

* keep VPS-1 as recoverable source
* do not partially switch users
* restore or discard failed target import safely
* retry only after issue analysis

Rules:

* migration must be reversible
* never overwrite original data
* cutover should occur only after validation passes

### C.17.8 Migration Execution Plan

Steps:

1. backup VPS-1
2. setup new backend/database
3. run dry-run migration
4. validate dry-run report
5. run real migration
6. validate target data
7. switch bot/backend
8. monitor system closely
9. keep rollback window active

### C.17.9 Migration Risks

#### C.17.9.1 Data Mismatch

Description:

* data mismatch between systems

Mitigation:

* mapping review
* sample validation
* quarantine uncertain rows

#### C.17.9.2 Lost Quota

Description:

* lost quota or incorrect remaining balances

Mitigation:

* conversion log
* quota reconciliation
* admin manual adjustment tools

#### C.17.9.3 User Confusion

Description:

* users may not understand new token-based access model after migration

Mitigation:

* clear messaging
* support guidance
* admin recovery tools

#### C.17.9.4 Incorrect Plan Assignment

Description:

* wrong mapping may assign incorrect plan to tokens

Impact:

* unfair quota or limits

Mitigation:

* log all mappings
* allow admin review and correction

#### C.17.9.5 Incorrect Entitlement Conversion

Description:

* converting user-based subscription to quota-based token may miscalculate value

Impact:

* users receive too much or too little quota

Mitigation:

* log all conversions
* allow admin manual adjustment
* validate sample users before full migration
---

# =========================================================
# D. PHASES
# =========================================================

## D. Phases

### D.1 Foundation MVP
Target:
- plans (DB-driven)
- tokens (secure, hashed)
- linked accounts (slot-based)
- total quota + daily cap logic
- core validation (backend enforced)
- secure token handling
- dynamic message + button system

Modules:
- C.1
- C.2
- C.3
- C.5
- part of C.10
- part of C.14

---

### D.1.X Phase-1 Build Lock Checklist
Before coding is considered aligned, implementation must reflect these locked rules:

* per-token + per-Telegram-account daily cap
* 60-second duplicate protection window
* deny new linking when max linked accounts is reached; direct user to contact admin
* no time-based expiry for standard plans
* Telegram Stars auto activation
* admin quota restore with dedicated audit trail

This checklist is mandatory for backend, WebApp, and bot integration prompts.
- backend
- Telegram bot
- WebApp admin
- all implementation prompts

---

### D.2 Linked Account & Recovery
Target:
- add account (auto-link if slot available)
- deny linking when limit reached
- lost device recovery (admin reset)
- linked account inspection

Modules:
- C.4
- part of C.11
- part of C.15

---

### D.3 Payments and Activation
Target:
- Telegram Stars (auto approve)
- local manual payment
- OCR-assisted review (assistant only)
- admin approval flow
- token creation + activation

Modules:
- C.7
- part of C.9
- part of C.12
- part of C.14

---

### D.4 Request, Delivery & Entitlement Enforcement
Target:
- request validation (no quota deduction)
- delivery payload system
- commit-success atomic deduction
- commit-failure logging
- duplicate request protection

Modules:
- C.5
- C.10
- part of C.14
- part of C.16

---

### D.5 Admin System & Audit
Target:
- WebApp admin control layer
- quota restore tools
- linked account reset
- payment review UI
- audit logs
- system settings control

Modules:
- C.15
- part of C.11
- part of C.12

---

### D.6 Language and UX Refinement
Target:
- Burmese-first UX
- English toggle
- dynamic message templates
- button set system
- consistent status-to-UX mapping

Modules:
- C.8
- part of C.14
- part of C.15

---

### D.7 Legacy Discovery and Staging
Target:
- inspect legacy schema
- classify usable data
- design transformation rules
- staging import + cleanup

Modules:
- C.13
- part of C.17

---

### D.8 Migration and Cutover
Target:
- transform legacy → token-based system
- import into PostgreSQL
- validate quota correctness
- validate media delivery
- switch to new backend
- keep rollback-safe legacy window

Modules:
- C.17
- part of C.2
- part of C.6
- part of C.10

# =========================================================
# E. DEPENDENCIES
# =========================================================

## E. Dependencies

### E.1 Core Token Engine
Required before:
- request validation
- quota enforcement
- payment activation
- linked-account logic

---

### E.2 Linked Account Engine
Required before:
- multi-account enforcement
- recovery/reset flows
- request validation

---

### E.3 Payment Workflow
Required before:
- manual payment activation
- token generation
- entitlement assignment

---

### E.4 Audit Logging Layer
Required before:
- admin operations
- dispute handling
- quota restoration
- payment review

---

### E.5 Dynamic Content System
Required before:
- multilingual UX
- message rendering
- button rendering

---

### E.6 Backend API Layer
Required before:
- bot integration
- WebApp integration

Rules:
- ALL enforcement must go through backend
- bot/WebApp must not implement business rules independently

---

### E.7 Atomic Transaction Layer
Required before production:
- quota deduction
- request commit
- daily counter update

---

### E.8 WebApp Admin System
Required before:
- production support
- payment approval
- token management

---

### E.9 System Settings Engine
Required before:
- duplicate window control
- cooldown logic
- retry limits

---

### E.10 Legacy Migration Inputs
Required before migration:
- database backup
- schema mapping
- transformation rules

---

### E.11 Media Reference Validation
Required before cutover:
- confirm Telegram file references still valid

---

### E.12 Configuration Runtime Layer
Required before:
- dynamic plan loading
- message override
- button resolution

Rules:
- DB config overrides code defaults
- fallback must always exist

# =========================================================
# F. RISKS
# =========================================================

## F. Risks

### F.1 Token Abuse Risk
Risk:
- token sharing beyond intended usage

Mitigation:
- linked-account slot limits
- audit logs
- revoke/reissue tools

---

### F.2 Payment Fraud Risk
Risk:
- fake or manipulated payment proof

Mitigation:
- OCR as assistant only
- admin approval required
- audit logs

---

### F.3 Quota Integrity Risk
Risk:
- incorrect quota deduction

Mitigation:
- atomic commit-success transaction
- idempotent request handling
- audit logs

---

### F.4 Duplicate Request Risk
Risk:
- multiple rapid requests deduct quota

Mitigation:
- server-side duplicate window
- duplicate guard key

---

### F.5 Linked Account Limit Conflict
Risk:
- multiple users trying to link simultaneously

Mitigation:
- deny new linking when limit reached
- no auto replacement
- admin-controlled reset

---

### F.6 Delivery Failure Risk
Risk:
- file not delivered after validation

Mitigation:
- retry logic
- commit-failure logging
- no quota deduction on failure

---

### F.7 Backend Authority Risk
Risk:
- bot/WebApp bypass backend rules

Mitigation:
- strict API enforcement
- no client-side logic

---

### F.8 Configuration Risk
Risk:
- admin misconfiguration breaks system

Mitigation:
- validation rules
- fallback values
- audit logs

---

### F.9 Migration Risk
Risk:
- incorrect data conversion

Mitigation:
- staged migration
- validation checks
- audit logs

---

### F.10 Concurrency Risk
Risk:
- multiple requests causing inconsistent quota

Mitigation:
- DB transactions
- row locking
- idempotency

---

### F.11 UX-State Mismatch Risk
Risk:
- UI does not match backend state

Mitigation:
- backend controls message + buttons
- no client-side assumptions

---

### F.12 Admin Abuse Risk
Risk:
- excessive manual overrides

Mitigation:
- audit logs
- future admin role limits

# =========================================================
# G. FUTURE ADDITIONS QUEUE
# =========================================================

## G. Future Additions Queue

### G.1 PIN / 2-Step Verification
For sensitive actions.

---

### G.2 Family Plan Logic
Shared token with controlled slots.

---

### G.3 Promotional Tokens
Marketing campaigns and bonus quota.

---

### G.4 Category Restrictions
Plan-based content limitation.

---

### G.5 Analytics Dashboard
Usage, revenue, system insights.

---

### G.6 Anti-Abuse Scoring
Behavior-based risk detection.

---

### G.7 Queue System (BullMQ)
For delivery and background jobs.

---

### G.8 Redis Caching Layer
Performance optimization.

---

### G.9 Self-Service Account Reset
User-initiated limited reset.

---

### G.10 Migration Tools
Dry-run validation + reporting.

---

### G.11 Notification System
Advanced alerts and reminders.

# =========================================================
# H. PROMPT SOURCE AND IMPLEMENTATION FOCUS
# =========================================================

# =========================================================
# H.1 PROMPT SOURCE
# =========================================================

## H.1 Prompt Source

### H.1.1 Prompt Use Rule
This document is the source of truth for generating implementation prompts.

---

### H.1.2 Prompt Types
- backend implementation
- bot logic
- WebApp UI
- database design
- migration scripts
- audit/review prompts
- bug fixing

---

### H.1.3 Prompt Generation Rule
- always use latest version of document
- never use outdated logic

---

### H.1.4 Environment Rule
Use generic terms:
- backend server
- bot server
- database server

Avoid:
- VPS-1 / VPS-2 naming in code

---

### H.1.5 Migration Prompt Rules
- source = legacy SQLite
- target = PostgreSQL
- transform, do not copy
- preserve entitlement correctness

---

# =========================================================
# H.2 CURRENT IMPLEMENTATION FOCUS
# =========================================================

## H.2 Current Implementation Focus

- backend-first architecture
- PostgreSQL schema
- API contract implementation
- admin system
- migration planning

---

# =========================================================
# H.3 FINAL NOTE
# =========================================================

## H.3 Final Planning Note

This document is the evolving blueprint of MovieVirus.

Rules:
- update by section, not rewrite
- maintain consistency across modules
- preserve auditability
- prioritize correctness over shortcuts
