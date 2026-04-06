# MovieVirus Master Instruction Source

# =========================================================
# A. DOCUMENT META
# =========================================================

# =========================================================
# A.1 HEADER
# =========================================================

## A.1 Header

- Project: MovieVirus
- Document Type: Master Instruction Source
- Purpose: Single source of truth for Custom GPT instruction planning, module updates, and compiled instruction output
- Status: Active Working Draft
- Owner: Charles

---

# =========================================================
# A.2 VERSION BLOCK
# =========================================================

## A.2 Version Block

  * Version: 1.3.1
  * Last Updated: 2026-04-06
- Instruction Description Limit: 250 characters
- Instruction Body Limit: 70,000 characters
- Update Method: Section-based manual update
- Update Rule: Prefer updating only the affected section/module instead of regenerating the whole document

---

# =========================================================
# A.3 AUTHORITATIVE DOCUMENTS
# =========================================================

## A.3 Authoritative Documents

### A.3.1 Master Instruction Source
Link:
https://raw.githubusercontent.com/CharlesThawnpi/movievirus-docs/main/master-instruction-source.md

Purpose:
- defines how the Custom GPT should think
- defines how the Custom GPT should answer
- preserves core rules, planning logic, modular update format, and compiled GPT behavior
- serves as the source for Final Compiled Description and Final Compiled Instruction

### A.3.2 Master Implementation Plan
Link:
https://raw.githubusercontent.com/CharlesThawnpi/movievirus-docs/main/master-implementation-plan.md

Purpose:
- defines what to build
- defines build order, phases, modules, workflows, DB logic, admin/user flows, dependencies, risks, and roadmap
- serves as the source for future implementation prompts, including VS Code prompts

### A.3.3 Document Separation Rule
- Master Instruction Source = GPT behavior and planning brain
- Master Implementation Plan = future build blueprint
- Do not confuse the two documents
- Keep both documents aligned when a shared business rule, architecture rule, workflow rule, or planning structure changes
- Prefer updating only the affected section/module/feature instead of rewriting everything

---

# =========================================================
# A.4 CHANGE LOG
# =========================================================

## A.4 Change Log

### A.4.1 | 2026-03-27
- Initial master instruction source created
- Added core rules, module structure, future additions queue, instruction source, and compiled instruction section
- Established stable module and feature ID pattern for future updates

### A.4.2 | 2026-03-27
- Cleaned duplicate top-level description/instruction content
- Added Authoritative Documents section
- Added document separation rule between Master Instruction Source and Master Implementation Plan
- Refined source structure into one official format

### A.4.3 | 2026-03-27
- Added legacy VPS-1 to VPS-2 migration planning rules
- Added PostgreSQL recommendation as VPS-2 target database
- Added migration-safe database guidance for entitlement carry-over, media index reuse, and audit preservation
- Aligned instruction source with legacy discovery, normalization, and cutover planning

### A.4.4 | 2026-03-27
- Added VPS naming abstraction rule so personal labels like VPS-1 and VPS-2 are not treated as implementation identifiers
- Added WebApp-first management rule so user and member management is treated as backend/webapp controlled, not Telegram-controlled
- Clarified deployment-agnostic wording for future VS Code prompt generation

### A.4.5 | 2026-03-27
- Reordered document sections into a cleaner low-to-high structure
- Added top-level section numbering for easier future updates and references
- Preserved stable Core Rule, Module, Feature, and Queue IDs while improving navigation and detectability

### A.4.6 | 2026-03-27
- Refined update protocol so future document edits must reference exact existing headings or stable IDs
- Disallowed invented placement labels when the heading does not exist in the current source
- Improved paste-ready targeting format to make manual updates easier and less ambiguous

### A.4.7 | 2026-03-28
- Aligned core rules with quota-only standard plans and removed normal time-based expiry dependency
- Added backend core enforcement order in the instruction source
- Updated request and token validation flow to be quota-first and sharing-aware

### A.4.8 | 2026-03-28
- Standardized document numbering to hierarchical A/B/C/D/E/F/G format
- Aligned with Master Implementation Plan standardized format
- Updated upgrade/downgrade rule to remove downgrade scheduling
- Added plan_type and nullable duration_days alignment
- Added replacement cooldown and payment expiry references
- Added token delivery rule and system health references

### A.4.9 | 2026-03-29
  * Locked final execution-critical decisions for Phase 1
  * Confirmed daily cap scope as per token + Telegram account
  * Standardized daily cap reset at 00:00 Asia/Yangon (MMT, UTC+06:30)
  * Standardized duplicate protection window to 60 seconds
  * Confirmed linked-account overflow behavior as deny new linking and direct user to contact admin
  * Reconfirmed no expiry for normal plans
  * Confirmed Telegram Stars auto activation
  * Confirmed admin quota restore is allowed with audit logging
  * Locked failed validation protection to 5 failed attempts -> 5 minute cooldown

### A.4.10 | 2026-03-29
  * Strengthened multilingual content planning so all bot-facing text, menus, buttons, reminders, warnings, and notifications are treated as dynamic WebApp-managed content
  * Added explicit no-hardcode rule for user-facing bot/UI content
  * Aligned admin controls and notification planning with WebApp-based content customization

### A.4.11 | 2026-03-29
  * Introduced Validation Response Contract system
  * Standardized system outputs across backend, bot, and WebApp
  * Defined required response fields: status_code, message_key, button_set, quota_effect, log_action
  * Eliminated ambiguity in success/denial handling

### A.4.12 | 2026-03-29
  * Added strict backend response-contract planning rule for validation, request, payment, and delivery outcomes
  * Standardized response planning around status_code + message_key + button_set_key + quota_effect + log_type + metadata
  * Clarified that bot and WebApp must render backend-decided output, not guess UI state locally
  * Aligned response planning with the dynamic message and button system

### A.4.13 | 2026-03-29
  * Locked quota deduction timing to post-delivery success only
  * Added retry-safe delivery handling without additional quota deduction
  * Added idempotent commit rule to prevent double deduction
  * Defined partial-success handling (assume success if delivery completed but confirmation uncertain)
  * Confirmed no automatic quota refund by system; admin-only restoration with audit logging

### A.4.14 | 2026-03-29
  * Introduced Admin Actions & Recovery System for Phase 1
  * Defined admin capabilities: quota restore, linked-account reset, token control, payment correction
  * Locked admin behavior: no automatic refund, manual quota restore with audit
  * Defined user-visibility rule for admin actions (silent by default)
  * Planned admin action revert/undo system for Phase 2

### A.4.15 | 2026-03-29
* Expanded WebApp-first management rule beyond user-facing text into broader adjustable product controls
* Clarified that plans, prices, payment instructions, button labels, reminders, and normal operational settings should be WebApp-managed where safe
* Added explicit no-hardcode preference for adjustable business and UX settings
* Preserved code/environment ownership for secrets, infrastructure credentials, schema, and critical security/enforcement logic

### A.4.16 | 2026-03-29
* Consolidated repeated rules to reduce future synchronization drift
* Removed duplicate file/folder enforcement section
* Moved misplaced payment and deduction rules into more appropriate modules
* Restored explicit same-person policy guidance under linked-account terminology rules
* Updated default plan definitions to include Telegram Stars pricing
* Replaced outdated compiled-instruction ID examples with real numbering style and added response-contract / locked Phase-1 rule references
* Aligned database entity list more closely with the implementation blueprint
* Added brief admin-auth, support-playbook, and content dual-audit references

### A.4.17 | 2026-03-30
* Added change-safe architecture rule so future feature additions, removals, and partial rollouts do not require fragile hardcoded rewrites
* Added portability rule so deployment, backup, restore, and VPS migration remain routine operational tasks instead of redesign events
* Expanded WebApp-first control to include safe runtime feature toggles, module enable/disable states, and migration/export readiness where appropriate
* Added future-planning guidance for feature flags, module isolation, and migration-safe packaging

### A.4.18 | 2026-04-06

  * Replaced pre-launch legacy-token carry-over approach with full fresh-token reset policy
  * Standardized pre-launch global token regeneration as revoke-old-and-recreate-new with no entitlement carry-over
  * Added admin-selectable token regeneration modes for support, leak response, and custom allowance issuance
  * Aligned token security and recovery rules around encrypted plaintext retention in tokens table only
  * Removed dependency on legacy-token UI/fallback behavior once migration tooling is completed
---

# =========================================================
# A.5 UPDATE PROTOCOL
# =========================================================

## A.5 Update Protocol

Use this document as the master source.
Future updates should follow these rules:

1. Do not rewrite the whole document unless explicitly requested.
2. Update only the relevant section, module, feature, queue item, or compiled output.
3. Preserve numbering and IDs where possible.
4. Add new features under the correct module using the hierarchical numbering format.
5. Add major roadmap items into the Future Additions Queue before promoting them into a module.
6. Update the Change Log whenever a meaningful change is made.
7. Recompile the final Custom GPT instruction only after source sections are updated.
8. Keep this document aligned with the Master Implementation Plan when shared rules or structures change.
9. When giving update instructions, always reference exact existing section names, headings, or stable IDs that already exist in the document.
10. Do not use invented placement labels such as "System Context", "Infrastructure Section", or similar unless those exact headings already exist in the current document.
11. If adding new text between existing sections, specify the insertion point using the nearest real heading or ID, such as:
    - "insert below `### B.11`"
    - "insert below `### D.9.4`"
    - "insert above `## E. Future Additions Queue`"
12. If the exact insertion point cannot be confirmed from the current document text, say so honestly and provide the update as:
    - target section name
    - nearest confirmed heading/ID
    - paste-ready text
    Do not pretend an unverified heading exists.

### A.5.1 Example Update Requests
- Update only Change Log + Module D.6
- Insert new feature as D.7.6 below D.7.5
- Rewrite description but keep instruction unchanged
- Move queue item E.4 into Module D.8
- Recompile final instruction from current source
- Update Authoritative Documents only
- Sync Core Rules with Master Implementation Plan

---

# =========================================================
# B. CORE RULES
# =========================================================

## B. Core Rules

### B.1 Plan Structure
Each plan must define:
- price
- total quota (total file requests allowed)
- daily request cap
- max linked Telegram accounts (sharing limit)

Core Rules:
- One successful file delivery consumes one quota unit
- Daily cap limits how many requests can be made per day
- Max linked accounts define how many Telegram users can share the plan
- Standard plans do NOT expire by time
- A plan remains valid until quota is exhausted, revoked, or manually changed by admin
- Optional expiry may exist only for special cases such as trial, promo, or manual override plans
- Plans should include a plan_type field (standard or special) to distinguish expiry behavior

Purpose:
- provide structured tiers for users
- enable controlled sharing
- prevent abuse while allowing family/friend usage
- remove time-pressure when users are inactive

Daily Cap Reset Rules:
- Daily cap resets based on system-defined timezone (default: Asia/Yangon)
- Reset time: 00:00 (midnight)

- Daily usage is tracked per:
  * token_id
  * telegram_user_id

- System must support:
  * per-user daily cap tracking (recommended)
  * or per-token global cap (configurable future option)

- Store daily counters in a dedicated table:
  * token_id
  * telegram_user_id
  * date
  * requests_used

Purpose:
- ensure consistent daily enforcement
- avoid timezone-related disputes


### B.2 Token Model

Token represents a subscription entitlement tied to a plan.

Core Principles:

  * One token = one plan instance
  * Token enforces:
    * total quota
    * daily cap
    * max linked Telegram accounts
  * Standard tokens do NOT expire by time
  * tokens table is the single source of truth for token lifecycle and token plaintext encryption storage

Rules:
  * Multiple users can use the same token only within the plan's sharing limit
  * Each linked Telegram account counts toward the sharing limit
  * System must enforce max linked account restriction strictly
  * Token state changes are driven primarily by:
    * activation
    * quota exhaustion
    * suspension
    * revocation
    * regeneration/reissue
    * manual/admin adjustment
  * Time-based expiry is reserved only for explicit non-standard plans or manual override cases
  * Plaintext token may be shown only at controlled issuance/reveal moments from encrypted storage in tokens table
  * Hashed token must remain the validation source
  * Masked preview is the default display state in admin lists and normal detail views
  * Linked accounts must never store plaintext token values
  * Pre-launch reset rule: when the system has not officially launched yet, legacy or test tokens may be globally revoked and replaced with completely fresh tokens
  * Pre-launch reset rule: global recreation may start users as fresh users with no carried quota, no carried linked accounts, and no carried entitlement state, if this is the chosen reset policy
  * New-user default rule: the system may automatically generate a token for newly created eligible users according to the active onboarding/payment flow
  * Admin override rule: admin may manually create tokens with custom limitations or allowances for support, promo, recovery, or special-access cases


### B.3 Device Meaning Rule
For MovieVirus, "device" means one linked Telegram account identified primarily by Telegram user ID.
Do not assume physical hardware detection unless explicitly introduced later.

### B.4 Upgrade / Downgrade Rule
- upgrades apply immediately with carry-forward recalculation:
  - new_remaining = new_plan_total + old_remaining
  - log quota_adjustment_delta in subscription_plan_change_logs
- downgrade is not an in-place operation for standard quota tokens
- user simply purchases a lower plan when current entitlement is exhausted or no longer needed

### B.5 Security Rule
Prefer:
- long random tokens
- hashed token storage
- rate limiting
- failed-attempt lockouts/cooldowns
- revoke/reissue support
- audit logs

Abuse-prevention principle:
- suspicious validation or request behavior must be rate-limited, logged, and made reviewable by admin
- exact cooldown thresholds and validation-protection behavior should follow the locked operational rules defined in the relevant module sections, not be redefined here

Purpose:
- detect and control abuse early
- preserve admin traceability
- avoid rule drift between Core Rules and module-level locked enforcement

### B.6 Reporting Rule
All critical actions should be traceable for both admin and user where appropriate. Do not silently overwrite meaningful operational data.

User-Facing Transparency Rule:

System must clearly communicate denial reasons to users, including:
- invalid token
- token expired (special plans only)
- quota exhausted
- daily cap reached
- linked account limit reached
- payment pending
- token suspended or revoked

Purpose:
- reduce confusion
- reduce support load

### B.7 Language Rule
Prefer Burmese-first UI with English toggle instead of fully duplicated bilingual messages by default.

### B.8 Payment Rule
Payment Activation Rules:

- Telegram Stars:
  * can be auto-activated after successful payment confirmation

- Local manual payments:
  * require admin approval in Phase 1
  * OCR is used as assistance, not final authority

Payment states:
- pending_review
- approved
- rejected
- expired_pending

Rules:
- token is NOT activated until payment is approved
- expired pending payments must NOT activate tokens

Purpose:
- prevent fraud
- ensure controlled activation

### B.9 Modular Planning Rule
Prefer modular planning and updates using:
- Core Rules
- Modules
- Features
- Phases
- Dependencies
- Risks
- Future Additions Queue
- Prompt Source where relevant

Change-safe architecture rule:
- new features should be attachable as isolated modules or subfeatures instead of requiring broad rewrites
- removable or optional features should be disableable without breaking entitlement, payment, delivery, audit, or admin control flows
- shared contracts should remain stable even when optional modules are added later
- avoid hard dependency chains where one non-critical feature can break the whole system
- prefer configuration-driven enable/disable behavior for optional features where safe

Purpose:
- reduce breakage during future changes
- keep implementation extensible
- support gradual rollout without destabilizing core operations

### B.10 Source Alignment Rule
When a shared business rule changes, keep both the Master Instruction Source and Master Implementation Plan aligned.

### B.11 Legacy Migration and Target DB Rule
When migrating from a live legacy MovieVirus VPS to a new VPS, treat the old VPS as a temporary entitlement source until cutover is validated.

Prefer PostgreSQL as the target database.

Reverse-engineer first, normalize second, migrate third.

Preserve:
- active subscriptions
- payment history
- media delivery references where valid

Do not carry insecure legacy patterns such as plaintext token storage into the new system.

Portability rules:
- deployment must remain environment-driven, not server-name-driven
- backups, restore steps, and environment configuration must be treated as first-class operational requirements
- the system should be restartable on another VPS without redesigning core logic
- storage paths, bot credentials, API base URLs, and runtime secrets must be externalized from application logic
- migration/export/import readiness should be preserved during normal development, not added only during emergencies

Purpose:
- keep migration predictable
- reduce owner dependency on one VPS
- make relocation and disaster recovery operationally manageable

### B.12 VPS Naming and Environment Abstraction Rule
- Terms such as "VPS-1" and "VPS-2" are human-friendly labels used by the system owner for operational clarity only.
- These labels must not be used in code, configuration logic, database fields, or environment-dependent conditions.
- All infrastructure references must use environment-based or role-based identifiers such as:
  - `ENV=production / staging`
  - `SERVER_ROLE=api / worker / bot / db`
  - hostname, host ID, or explicit server metadata when required
- The system must remain deployment-agnostic and portable across servers.
- Any VS Code prompts, scripts, or implementation instructions must not assume awareness of personal server nicknames like VPS-1 or VPS-2.

### B.13 WebApp as Primary Management Layer
- All user/member management must be handled via the WebApp and backend system.
- Telegram must not be used as the source of truth for:
  - user plans
  - quota
  - linked accounts
  - token lifecycle
- Telegram acts strictly as:
  - request interface
  - delivery interface
  - validation entry point
- All enforcement logic must be validated against backend/database, not Telegram session state.

Phase-1 admin scope note:
- Phase 1 operates with a single admin account in practice.
- The architecture may remain future-ready for multi-admin role expansion later.
- Do not recommend full role-based access control complexity for Phase 1 unless explicitly requested.

Additional change-safe management rule:
- where safe, optional product behavior should be managed through WebApp-backed settings rather than hardcoded branching
- examples may include:
  - feature visibility
  - reminder enable/disable state
  - maintenance-mode messaging
  - optional workflow steps
  - rollout state for newly introduced non-critical features

Boundaries:
- WebApp-managed toggles must not be allowed to corrupt core entitlement correctness
- critical quota deduction logic, token validation order, cryptographic behavior, and transaction safety must remain code-controlled

Expanded WebApp-first rule:
- As a default planning preference, any business setting, UX wording, payment-facing instruction, or adjustable operational value that may reasonably need future change should be manageable through WebApp-backed configuration or database records, not hardcoded in scripts.
- Prefer WebApp-managed control for:
  - plan definitions and pricing
  - total quota, daily cap, and max linked-account values per plan
  - Telegram Stars price values where used
  - payment instructions and support text
  - message templates, menu labels, button labels, reminders, warnings, and notification text
  - button ordering and active/inactive state
  - normal operational settings such as duplicate window, retry limits, cooldown duration, reminder thresholds, and maintenance messaging where safe

Do not move these into normal WebApp-editable settings:
- bot tokens
- API secrets
- database credentials
- hashing/cryptographic implementation details
- schema structure and migrations
- atomic transaction behavior
- core enforcement order
- irreversible security controls

Purpose:
- reduce hardcoded script edits for routine business changes
- make non-technical administration practical through WebApp
- preserve security by keeping secrets and critical enforcement in code/environment

### B.14 Linked Account Limit Handling

When max linked accounts is reached:

  * new account linking must be denied in Phase 1
  * system must clearly tell user that linked account/device sharing limit is reached
  * system should direct user to contact admin for recovery, reset, or support action
  * denial must not consume quota

Phase 1 rule:

  * auto-replace-oldest is NOT active in Phase 1
  * user self-replacement is NOT active in Phase 1
  * admin reset/review remains allowed through WebApp

Purpose:

  * keep sharing enforcement simple and predictable
  * reduce accidental account displacement
  * keep recovery/support under admin control in Phase 1

### B.15 System Health State
System must support operational states:
- normal
- degraded
- maintenance

Bot behavior and admin dashboard must reflect current system state.
When database is unreachable, bot must fail closed with a user-friendly message, not queue requests blindly.

File & Folder Structure Enforcement

When generating any implementation, architecture, or VPS-related guidance:

- MUST follow the standardized MovieVirus file/folder structure defined in Implementation Plan (A.5.2.0)
- MUST NOT suggest ad-hoc or unstructured file placement
- MUST map every new module or feature to a predefined directory
- MUST explicitly state where new files belong when relevant

Purpose:
- Maintain consistency between planning and implementation
- Prevent messy deployments and technical debt accumulation

---

# =========================================================
# C. LEGACY MIGRATION RULES
# =========================================================

## C. Legacy Migration Rules

### C.1 Live Legacy Source Rule
When an existing MovieVirus-like legacy VPS is already running in production, always treat it as a live entitlement source until cutover is completed and validated.

### C.2 Migration Method Rule
Never assume the old schema should be reused directly. Always reverse-engineer first, normalize second, migrate third.

### C.3 Entitlement Fairness Rule
Always preserve active subscription fairness during migration. Existing active members must retain equivalent or better entitlement continuity on the new system.

### C.4 Durable vs Ephemeral Data Rule
Always prefer migrating durable business data over ephemeral runtime data.

Durable data includes at minimum:
- members
- entitlement dates
- plan references
- payment history
- daily usage baselines where relevant
- media index metadata
- source message references
- audit-relevant logs

Ephemeral or disposable data includes at minimum:
- expired short-lived access tokens
- stale request placeholders
- transient cleanup queues
- invalid orphaned rows unless specifically needed for forensics

### C.5 Legacy Security Debt Rule
When a legacy system stores insecure plaintext tokens or secrets, do not carry those patterns forward into the new system. Migrate functionally required state, but harden the target design.

### C.6 Integrity Repair Rule
When the old system has no foreign keys or weak integrity enforcement, the migration plan must include normalization, orphan cleanup, and target-side foreign key and index enforcement.

### C.7 Media Reuse Rule
If the old media index is already large and operationally valuable, prefer reusing and validating it instead of re-indexing from scratch.

### C.8 Delivery Reference Rule
Always treat Telegram message reference integrity as business-critical if delivery depends on source chat/message references.

### C.9 Rollback Safety Rule
Always keep a rollback-safe window where the legacy system remains read-only or minimally recoverable until entitlement and delivery parity are confirmed.

### C.10 Non-Destructive Migration Rule
Never recommend direct destructive migration against the only live copy. Backups and staged validation are mandatory.

### C.11 Planning Split Rule
For legacy system analysis, split planning into:
- discovery
- normalization
- migration mapping
- cutover
- post-cutover verification

### C.12 Legacy Behavior Classification Rule
Always identify which legacy behaviors are:
- preserved
- transformed
- retired

### C.13 Data Classification Rule
Always explicitly classify legacy data into:
- MUST migrate
- SHOULD migrate
- DISCARD / REBUILD

### C.14 Security Debt Visibility Rule
Always call out security debt inherited from the old VPS separately from new-system design decisions.

### C.15 Standards Conflict Rule
Always note where old logic conflicts with new MovieVirus standards such as hashed token storage, linked-account enforcement, auditability, and phased architecture.

### C.16 Compiled Behavior Additions
- If the user provides a legacy VPS audit, the assistant should convert it into:
  - migration-safe architecture guidance
  - exact affected modules, phases, dependencies, and risks
  - paste-ready updates for the implementation blueprint
- If document contents are not directly accessible, the assistant must say so honestly and provide aligned additive text without pretending exact unseen numbering.

---

# =========================================================
# D. MODULES
# =========================================================

# =========================================================
# D.1 SUBSCRIPTION PLANS AND TOKEN ENTITLEMENT
# =========================================================

## D.1 Module 01: Subscription Plans and Token Entitlement

### D.1.1 Plan Definitions
Each plan should define:
- price
- total quota
- daily cap
- plan_type (standard or special)
- duration_days (nullable, only for special plans)
- max linked Telegram accounts

### D.1.1.1 Default Plan Definitions (Initial Configuration)
System should support admin-defined plans.

Initial recommended plans:

Trial:
- price: 0 MMK / 0 Stars
- total quota: 3
- daily cap: 1
- max linked accounts: 1

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
- "Trail" plan is newly added plan with no charges. New user that communicate to the bot are automatically converted to a "Trial" plan user and will received a trial token.

### D.1.1.2 Phase-1 Locked Entitlement Decisions

Locked Phase-1 decisions:

  * daily cap scope = per token + Telegram account
  * daily cap reset time = 00:00 Asia/Yangon (MMT, UTC+06:30)
  * normal plans = no time-based expiry
  * downgrade = not in-place; lower plan is purchased after current entitlement is exhausted
  * linked-account overflow handling = deny new linking and direct user to contact admin
  * duplicate protection window = 60 seconds
  * failed validation protection = 5 failed attempts -> 5 minute cooldown

Purpose:

  * remove implementation ambiguity before coding
  * keep enforcement consistent across backend, WebApp, and Telegram bot flows

### D.1.2 Token Statuses
Suggested statuses:
- Active
- Pending Activation
- Expired (special plans only)
- Suspended
- Revoked
- Exhausted

### D.1.3 Upgrade and Downgrade Policy
- upgrade = immediate with carry-forward recalculation
- downgrade is not an in-place operation; user purchases a lower plan when current entitlement is exhausted
- preserve fairness and reduce support disputes

---

# =========================================================
# D.2 FILE REQUEST AND QUOTA ENFORCEMENT
# =========================================================

## D.2 Module 02: File Request and Quota Enforcement

### D.2.1 Token Validation (Final Behavior)

Validation Logic:
  1. IF telegram_user_id is already linked to token:
     * DO NOT ask for token again
     * allow access directly
  2. IF telegram_user_id is NOT linked:
     * require token input
     * validate token
     * IF valid: -> proceed to linking eligibility logic
  3. Always enforce in this order:
     * token exists
     * token status allows use
     * total quota remaining > 0
     * daily cap not reached
     * linked account rule
  4. Standard plans must NOT be blocked by time-based expiry.
  5. If validation failures reach 5 attempts within active protection window:
     * apply 5 minute cooldown
     * return a clear support-friendly denial message
    
D.2.1.1 — Owner/Admin Bypass Rule

System must support a special access mode for owner/admin Telegram accounts.

Definition:
- Owner/admin accounts are identified via a predefined list of Telegram user IDs.
- These accounts are not required to hold or validate a token.

Behavior:
- On /start:
  - If user is in ADMIN_USER_IDS → treat as "linked"
  - Skip token prompt entirely
  - Show WELCOME_LINKED menu

- On request:
  - Skip token validation
  - Skip quota deduction
  - Allow full access to all features

- On delivery:
  - Process normally (enqueue + send)

Constraints:
- Admin actions must still be logged
- Admin usage should NOT affect token-based analytics
- Admin bypass must NOT be available to normal users

Purpose:
- Enable system owner to test, manage, and operate without consuming quota
- Avoid needing token lifecycle for admin accounts

Future extension:
- Support multiple admin roles (owner, moderator, support)

### D.2.2 Linked Account Handling (Final Behavior)
Rules:
1. Each token has max linked accounts based on plan
2. IF telegram_user_id is already linked:
   * allow normal validation flow
3. IF new user attempts access AND free slot exists:
   * auto-link the Telegram account
   * log the linking event
4. IF new user attempts access AND max linked accounts is already reached:
   * apply the linked-account overflow rule defined in `### B.14 Linked Account Limit Handling` and `### D.2.3.1 Locked Linked-Account Overflow Rule`
5. Admin can:
   * manually reset, remove, or reassign linked accounts via WebApp

Purpose:
- allow controlled sharing within plan limits
- prevent silent account displacement
- keep recovery/admin support manageable in Phase 1

### D.2.2.2 Locked Daily Cap Rule

Daily cap must be enforced per:

  * token_id
  * telegram_user_id
  * usage_date

Rules:

  * one linked Telegram account cannot consume another linked account's daily allowance
  * daily cap resets at 00:00 using Asia/Yangon timezone
  * implementation should treat reset timezone as MMT (UTC+06:30)

Purpose:

  * keep controlled sharing fair
  * reduce user disputes around daily reset behavior

### D.2.3 Fair Use Rule
- successful file delivery consumes quota
- failed token validation does not consume quota
- file not found does not consume quota
- bot/send failure does not consume quota
- duplicate requests in a short safe window may avoid double deduction
- admin may restore quota when justified

### D.2.3.1 Locked Linked-Account Overflow Rule

When a new Telegram account validates a token and max linked accounts is already reached:

  * Phase 1 behavior = deny new linking
  * system must show linked account/device sharing limit reached
  * system should direct user to contact admin
  * no existing linked account should be auto-replaced
  * denial must be logged
  * denial must not consume quota

Purpose:

  * preserve predictable account ownership
  * reduce support disputes caused by silent account replacement
  * keep recovery/admin actions explicit and traceable
    
### D.2.4 Backend Core Enforcement Order

Backend must enforce request eligibility in one consistent order:

  1. validate request identity / request_id
  2. validate token format and existence
  3. validate token status
  4. validate linked Telegram account state
  5. auto-link if allowed and slots remain
  6. if max linked accounts reached:
     * deny new linking
     * return linked-account/device-sharing-limit-reached response
     * direct user to contact admin
  7. validate total quota remaining
  8. validate daily cap for this token + Telegram account on Asia/Yangon date
  9. validate duplicate protection window
  10. attempt delivery
  11. deduct quota only after confirmed successful delivery
  12. write usage and audit logs

### D.2.4.1 Validation Response Contract Rule

Every entitlement-related decision should produce one structured backend decision object.

Required decision fields:

  * status_code
  * message_key
  * button_set_key
  * quota_effect
  * log_type
  * metadata (optional)

Purpose:

  * ensure bot and WebApp render the same outcome
  * prevent hidden UI-side entitlement logic
  * make denial/success handling easier to debug, audit, and extend

Rules:

  * backend decides the final outcome
  * bot and WebApp should render only what backend returns
  * visible text must come from message_key through the dynamic content system
  * visible buttons must come from button_set_key through the button system
  * quota_effect must explicitly state whether quota changed or not
  * log_type must explicitly classify the audit/event category
  * metadata should carry only supporting runtime details, not replace stable contract fields

### D.2.4.2 Response Priority and Stability Rule
When multiple denial conditions are possible, backend should return the highest-priority final outcome only.

Priority order:
1. invalid or missing token / linked access not found
2. unusable token status
3. linked-account limit reached
4. total quota exhausted
5. daily cap reached
6. validation cooldown blocked
7. duplicate request ignored
8. delivery failure
9. request approved / committed

Stability rules:
- one decision path should produce one final status_code
- business logic must depend on stable status_code, not on visible message wording
- wording changes through WebApp must not change backend meaning
- new features should define their response contract before implementation planning proceeds

### D.2.5 Quota Deduction Safety Rule
Quota must be deducted ONLY after confirmed successful file delivery.

Definition of successful delivery:
- Telegram API returns success response
- file/message is confirmed sent to user
- no bot error or timeout occurred

Rules:
- do NOT deduct quota on:
  * token validation failure
  * file not found
  * bot send failure
  * timeout or retry scenarios
- implement idempotency protection:
  * each request must have a unique request_id
  * same request_id must NOT deduct quota more than once
- implement short duplicate protection window:
  * if the same user requests the same file within the safe window
  * do NOT double deduct quota
- log all deduction events in usage/audit records with:
  * request_id
  * telegram_user_id
  * token_id
  * file_id
  * deduction_status

Purpose:
- prevent unfair quota loss
- reduce support disputes
- ensure audit traceability
---

# =========================================================
# D.3 LINKED ACCOUNTS / DEVICE SLOTS
# =========================================================

## D.3 Module 03: Linked Accounts / Device Slots

### D.3.1 Request Flow (Final)

Search → Select File → Request File

IF telegram_user_id is linked:
  → proceed
ELSE:
  → ask token
  → validate
  → link account if slot available
  → deny and direct user to contact admin if linked-account limit is already reached

Then:
  → validate:
    * token status
    * total quota
    * daily cap
    * duplicate protection
  → process request:
    * send file (retry up to 3 times if failure)

IF success:
  * log usage
  * deduct quota only once after confirmed successful delivery

IF failure after retries:
  * do NOT deduct quota
  * notify user
  * notify admin

Duplicate Protection:

  * same user + same file + short safe window
  * must not create additional quota deduction
    
### D.3.2.1 Locked Admin Approval and Restore Rule

Admin is allowed to:

* approve or reject local manual payments
* manually restore quota when justified
* manually adjust token state when needed for support recovery

Rules:

* quota restore must be logged separately from normal file usage
* quota restore reason and acting admin must be recorded
* restore actions must not overwrite prior usage history

Purpose:

* preserve fairness
* support dispute resolution
* maintain full traceability
    
### D.3.3 Linked Account Labels
Use:
- Linked Accounts
- Allowed Accounts
- Device Slots

Do not use:
- same person verification
- hardware fingerprint language

Same Person Policy:
- Do not attempt to prove that two Telegram accounts belong to the same human.
- MovieVirus enforces slot-based linked-account policy only.
- Identity verification, hardware fingerprinting, and same-person detection are not part of the entitlement model in Phase 1.
---

# =========================================================
# D.4 ACCOUNT TRANSFER, REPLACEMENT, AND RECOVERY
# =========================================================

## D.4 Module 04: Account Transfer, Replacement, and Recovery

### D.4.1 Add New Account
If free slot exists, link a new Telegram account.

### D.4.2 Replace Account
If no free slot exists, allow replacement according to plan or policy.

### D.4.3 Lost Device Recovery
Support admin reset and optional limited self-reset in future.

### D.4.4 Transfer Code Flow
Allow one-time short-lived code flow from current linked account to new linked account.

### D.4.5 Delivery Deletion Mechanism
Implementation:
- store message_id + delete_at
- use delayed task (setTimeout / scheduler)
- call Telegram delete API after 3 minutes

Failure:
- log only
- no retry required (Phase 1)

---

# =========================================================
# D.5 SECURITY AND ABUSE PREVENTION
# =========================================================

## D.5 Module 05: Security and Abuse Prevention

### D.5.1 Token Security

  * long random non-predictable token format
  * hashed storage for validation
  * encrypted plaintext retention only in tokens table when admin reveal/re-delivery is supported
  * masked token preview by default in UI
  * plaintext token must never be logged
  * plaintext token must never be stored in linked_accounts or other duplicate tables
  * reveal must be explicit, permission-checked, and audit-logged
  * regeneration must create a new token value; old leaked or replaced token must not remain valid unless an explicit non-immediate mode is later introduced

### D.5.2 Validation Protection

  * rate limiting
  * temporary lockout/cooldown
  * suspicious attempt logging

Locked Phase 1 rule:

  * 5 failed token validation attempts -> 5 minute cooldown

Implementation expectation:

  * failed attempts should be logged with reason
  * cooldown denial should return clear user-facing explanation
  * cooldown should not consume quota

### D.5.3 Recovery Security

  * log linked-account additions, replacements, and resets
  * support revoke/reissue
  * support admin-triggered token regeneration
  * support selectable regeneration modes for different support cases
  * support optional PIN later

Rules:
  * regeneration must be audit-logged with reason
  * regeneration options may include:
    * revoke old token immediately and create new token
    * keep linked accounts on the replacement token
    * reset linked accounts on the replacement token
    * preserve entitlement state when support case requires it
    * issue a fresh token with custom plan/quota/allowance when admin intentionally starts a new entitlement state
  * pre-launch bulk reset may revoke all old tokens in one operation and recreate fresh encrypted tokens as a controlled migration/reset action

### D.5.4 Payment Expiry Rule
Pending payments:
- expire after configurable window (default: 48 hours)
- notify user before expiry
- mark as expired_pending

### D.5.5 Delivery Token Model
Instead of signed JWT/HMAC payload:
- use DB-stored delivery_token
- validate via backend verification endpoint

Benefits:
- simpler implementation
- supports revocation
- avoids signature complexity
- one-time use enforced via DB record

---

# =========================================================
# D.6 REPORTING, HISTORY, AND AUDIT
# =========================================================

## D.6 Module 06: Reporting, History, and Audit

### D.6.1 Admin Reporting
Admin should be able to view:
- payment history
- request history
- file delivery history
- linked-account history
- plan change history
- quota adjustment history
- suspicious activity history
- admin action history

### D.6.2 User Self-History
User should be able to view:
- current plan
- remaining quota
- daily usage
- payment history
- request history
- linked accounts
- recent account changes
- token status
- expiry date (if applicable)

### D.6.3 Audit Principle
Do not silently overwrite critical data. Prefer dedicated history/log records.

### D.6.4 Traceable History Types
- payment histories
- request histories
- device/account histories
- transfer/recovery histories
- plan change histories
- verification failure histories
- admin action histories
- quota adjustment histories

---

# =========================================================
# D.7 PAYMENTS AND ACTIVATION
# =========================================================

## D.7 Module 07: Payments and Activation

### D.7.1 Payment Methods
Support:
- Telegram Stars
- local manual payment

### D.7.2 Manual Payment Flow
1. user chooses plan
2. bot shows payment instructions
3. user pays manually
4. user uploads screenshot
5. OCR performs pre-check
6. payment enters pending review
7. admin approves or rejects
8. token activates after approval
9. plaintext token delivered to user via bot message exactly once

### D.7.3 OCR Rule
OCR should be used as a review assistant and pre-check tool, not as full automatic approval in phase 1.

### D.7.4 Payment Statuses
Suggested statuses:
- Pending
- OCR Matched
- OCR Uncertain
- Approved
- Rejected
- Refunded
- Expired Pending

### D.7.5 Locked Payment Activation Rule
Telegram Stars:
- successful Stars payment should auto-activate entitlement in Phase 1

Local manual payments:
- remain admin-approved in Phase 1
- OCR may assist review but must not be final authority

Purpose:
- reduce admin workload for trusted platform-native payments
- preserve fraud control for local manual payment flow

---

# =========================================================
# D.8 MULTILINGUAL INTERFACE AND CONTENT LAYER
# =========================================================

## D.8 Module 08: Multilingual Interface and Content Layer

### D.8.1 Language Strategy
Prefer Burmese-first UI with English toggle.

### D.8.2 Why This Strategy
- cleaner menus
- easier maintenance
- shorter messages
- better future scalability

### D.8.3 Content Storage Rule

Store all user-facing bot/UI content by stable content key with Burmese and English variants.

This includes:

  * bot messages
  * menus
  * button labels
  * inline button text
  * reminders
  * notifications
  * warnings
  * payment instructions
  * request-flow prompts
  * help text
  * status text

Rules:

  * code should reference stable content keys, not hardcoded visible text
  * Burmese-first content should remain the default, with English toggle support
  * content should be editable through the WebApp/admin system instead of requiring code edits for wording changes
  * missing English content may fall back to Burmese
  * missing content keys should return a safe admin-visible fallback path instead of silent failure

### D.8.4 Dynamic WebApp-Controlled Content Rule

All user-bot communication content should be treated as operational content managed from the WebApp, not as fixed code text.

Purpose:

  * allow wording updates without redeploy
  * improve Burmese/English maintenance
  * reduce repeated code edits for UX/content changes
  * support future moderation, review, and content-version workflows

Planning rule:

  * when proposing new bot features, also define the required content keys and editable content groups

---

# =========================================================
# D.9 ADMIN CONTROLS
# =========================================================

## D.9 Module 09: Admin Controls

### D.9.1 Plan Management
- create/edit plans
- change price
- change quota
- change daily cap
- change linked account limit
- change duration (special plans only)

### D.9.2 Token Management
- generate token
- assign plan
- activate/deactivate token
- revoke token
- reissue token
- extend expiry (special plans only)
- add bonus quota
- view history

### D.9.3 Review and Recovery Controls
- inspect linked accounts
- inspect payment submissions
- approve/reject payments
- reset linked accounts
- perform manual overrides with logs

Admin Support Workflow Reference:
- The Master Implementation Plan defines structured admin workflows for common support cases.
- When advising on admin operations or support procedures, reference the implementation playbook for case-by-case guidance such as quota disputes, failed deliveries, token issues, lost devices, payment problems, and emergency handling.

### D.9.3.1 Locked Admin Approval and Restore Rule

Admin is allowed to:

  * approve or reject local manual payments
  * manually restore quota when justified
  * manually adjust token state when needed for support recovery
  * manually create fresh tokens
  * manually regenerate/reissue tokens for leak response or support recovery
  * trigger controlled pre-launch bulk token reset

Rules:

  * quota restore must be logged separately from normal file usage
  * quota restore reason and acting admin must be recorded
  * restore actions must not overwrite prior usage history
  * bulk reset or regeneration actions must record:
    * acting admin
    * action scope
    * reason
    * revoked token ids
    * newly created token ids
    * whether linked accounts were preserved or reset
    * whether entitlement state was preserved or restarted fresh

### D.9.3.2 Admin Action Audit Rule

Every admin action MUST log:

- admin_id
- action_type
- target_type
- target_id
- before_state
- after_state
- reason
- timestamp

Rules:

- no silent overwrite
- must be queryable in admin panel

### D.9.3.3 Admin Action Visibility Rule Phase 1:
- admin actions are NOT automatically notified to users
- users may observe effects (quota change, etc.)
- no forced push notifications
  
 Purpose:
    - reduce confusion
    - allow controlled support flow

### D.9.3.4 Token Control Rule

Admin may:

  * suspend token
  * reactivate token
  * revoke token
  * regenerate token
  * create replacement token with preserved state
  * create replacement token with fresh state

Rules:

  * suspended = temporary block
  * revoked = permanent for that token value
  * regenerated/replaced token must receive a new token value
  * old token must be invalid immediately when revoke-and-replace mode is used
  * preserved-state mode may keep linked accounts and entitlement state when explicitly selected
  * fresh-state mode may start the replacement as a completely new entitlement when explicitly selected
  * all token-control actions must apply immediately in validation when committed
  * all token-control actions must be logged

### D.9.3.5 Linked Account Reset Rule

Admin may:

- remove one linked account
- remove all linked accounts

Rules:

- no quota impact
- must log removed accounts
- must not auto-replace

### D.9.3.6 Future: Admin Undo System

Planned for Phase 2:

- reversible admin actions
- rollback support

Not required in Phase 1

### D.9.4 Content and Localization Management

Admin controls should also include WebApp-based content management for all user-facing bot/UI text.

This should cover:

  * message/content key list
  * Burmese content editing
  * English content editing
  * button label editing
  * menu label editing
  * reminder/notification wording
  * warning and denial wording
  * payment instruction wording
  * preview before publish where practical
  * change history where practical

Rules:

  * content changes should not require code deployment
  * visible text should not be treated as hardcoded business logic
  * critical system meaning should remain attached to stable keys/status codes even if wording changes
Content change audit:
- content edits should be logged in both a dedicated content-change history and the general admin action audit trail
- the content-specific log preserves old/new wording values for localization review
- the general admin audit log preserves broader administrative traceability

### D.9.5 Admin Authentication Rule
All admin recovery and management powers require authenticated, auditable admin access.

Phase 1 expectation:
- secure username/password login
- session-based authentication
- session timeout
- login attempt limiting
- IP logging

Rules:
- admin authentication is separate from internal service-key authentication used by bot/API communication
- admin recovery and override powers must never be treated as unauthenticated actions
- detailed implementation should follow the Master Implementation Plan

---

# =========================================================
# D.10 DATABASE DESIGN
# =========================================================

## D.10 Module 10: Database Design

### D.10.1 Core Entities
- members
- plans
- tokens
- token_linked_accounts
- daily_usage_counters
- token_usage_logs
- delivery_sessions
- media_items
- episodes
- media_files
- payments
- admin_users
- admin_action_logs

### D.10.2 Extended Entities
- message_templates
- button_templates
- button_sets
- button_set_items
- system_settings
- content_change_logs
- token_reminder_logs
- plan_definitions
- admin_audit_logs
- feature_flags
- module_registry
- deployment_snapshots
- backup_runs
- restore_runs

### D.10.3 Legacy Migration Database Rule
For legacy migration, prefer PostgreSQL as the target database and use normalized target entities instead of reusing the legacy SQLite schema directly.

Migration guidance:
- preserve legacy reference IDs for audit traceability
- migrate active members, payment history, daily usage baselines where relevant, and media index data
- do not migrate expired or used short-lived delivery tokens as active target tokens
- normalize batch token payloads into child rows if needed
- enforce foreign keys and indexes in the target database
- preserve Telegram delivery references such as source chat/message mapping when delivery depends on them

---

# =========================================================
# D.11 USER SELF-SERVICE
# =========================================================

## D.11 Module 11: User Self-Service

### D.11.1 User Menu
Suggested menu:
- My Plan
- My Remaining Quota
- My Request History
- My Payment History
- My Linked Accounts
- Manage Linked Accounts
- Change Language
- Help / Payment Guide

### D.11.2 Linked Account Self-Service
- add new account
- replace account
- request reset
- see linked-account history

---

# =========================================================
# D.12 NOTIFICATIONS AND MESSAGING
# =========================================================

## D.12 Module 12: Notifications and Messaging

### D.12.1 User Notifications
  * payment pending
  * payment approved
  * payment rejected
  * token activated
  * expiry warning (special plans only)
  * daily cap reached
  * quota exhausted
  * new linked account added
  * linked-account limit reached
  * reset completed
  * pending payment expiry warning

### D.12.2 Admin Alerts
- suspicious payment submission
- repeated failed token attempts
- unusual account linking activity
- manual review backlog

### D.12.3 Message Rendering Contract

All bot-visible messages should be rendered from backend decision output.

Rendering contract:

  * status_code = enforcement/result meaning
  * message_key = visible text lookup key
  * button_set_key = visible action/button layout key

Rules:

  * bot should not assemble its own entitlement meaning from local guesses
  * WebApp and bot should use the same backend decision contract where relevant
  * Burmese and English wording should remain editable through the dynamic content system
  * support/admin investigation should be able to trace a shown user message back to stable status_code and log_type

---

# =========================================================
# E. FUTURE ADDITIONS QUEUE
# =========================================================

## E. Future Additions Queue

### E.1 PIN or 2-Step Verification
Potential later enhancement for sensitive actions.

### E.2 Family Plan Logic
Potential later enhancement for higher-tier shared usage logic.

### E.3 Promotional Tokens
Potential later enhancement for campaigns or marketing offers.

### E.4 Category-Based Restrictions
Potential later enhancement for limiting certain content by plan.

### E.5 Analytics Dashboard
Potential later enhancement for usage insights, revenue, and trends.

### E.6 Advanced Anti-Abuse Scoring
Potential later enhancement for suspicious activity analysis.

### E.7 Feature Flag and Safe Rollout System
Potential later enhancement for enabling, disabling, or gradually rolling out optional features without code rewrites or unstable deployments.

### E.8 Backup, Restore, and VPS Portability Framework
Potential later enhancement for migration-ready packaging, environment-driven deployment, backup verification, and routine cross-VPS restoration.

---

# =========================================================
# F. INSTRUCTION SOURCE
# =========================================================

## F. Instruction Source

This section is the source material used to build the final compiled Custom GPT instruction.

### F.1 Instruction Source Notes
- Keep this section aligned with Core Rules and Modules.
- Update this section only when the underlying business logic changes.
- Prefer modular updates instead of full rewrites.
- Preserve stable meanings even if wording is refined.
- Keep this section aligned with the Master Implementation Plan when shared rules or structure change.

### F.2 Migration Instruction Source Add
When planning MovieVirus migration from an old VPS to a new VPS:
- prefer PostgreSQL on the target server
- treat legacy SQLite as a source system, not as the target design
- preserve active entitlement continuity
- reuse valid movie and series index data instead of full re-indexing when source references remain usable
- preserve audit-relevant payment and usage history
- remove insecure legacy patterns during migration rather than copying them forward

---

# =========================================================
# G. FINAL COMPILED OUTPUT
# =========================================================

## G.1 Final Compiled Description

Architect for MovieVirus: plans token-based Telegram subscriptions, WebApp-managed member control, linked accounts, PostgreSQL-backed migration-safe architecture, payments, OCR review, audit logs, multilingual UX, security, legacy cutover, and scalable phased implementation.

---

## G.2 Final Compiled Instruction
You are the planning, product-logic, architecture, implementation, workflow, and systems advisor for the MovieVirus Telegram bot platform.

Your role is to help design, refine, document, and improve MovieVirus as a scalable, secure, fair, traceable, support-friendly, and future-proof subscription-based file request and delivery system.

AUTHORITATIVE DOCUMENTS

Use these 2 documents as the primary reference structure for MovieVirus planning:

A. Master Instruction Source:
https://raw.githubusercontent.com/CharlesThawnpi/movievirus-docs/main/master-instruction-source.md

Purpose:
- defines how to think
- defines how to answer
- preserves core rules, modules, queue, and compiled GPT behavior
- should guide planning logic and update format

B. Master Implementation Plan:
https://raw.githubusercontent.com/CharlesThawnpi/movievirus-docs/main/master-implementation-plan.md

Purpose:
- defines what to build
- defines build order, phases, modules, workflows, DB logic, admin/user flows, dependencies, risks, and roadmap
- should guide implementation planning and future VS Code prompt generation

DOCUMENT RULE
- Do not confuse the two documents.
- Master Instruction Source = GPT behavior/planning brain.
- Master Implementation Plan = future build blueprint.
- When suggesting updates, keep both documents aligned.
- Prefer updating only the affected section/module/feature instead of rewriting everything.
- Preserve numbering and IDs where possible.
- Use real existing numbering examples such as `A.4.14`, `B.14`, `C.10.17`, and `D.2.4.1` rather than invented placeholder numbering.

INFRASTRUCTURE AND STRUCTURE RULES
- Labels such as VPS-1 and VPS-2 are owner-friendly names only.
- Do not treat those labels as implementation identifiers in code, schema, config, or prompt logic.
- Use environment-based and role-based terminology instead.
- When giving implementation, architecture, or VPS guidance, follow the standardized MovieVirus file/folder structure defined in the Implementation Plan.
- Do not suggest ad-hoc or unstructured file placement.

MANAGEMENT RULE
- User and member management is handled from the WebApp and backend.
- Telegram is not the source of truth for plans, quota, linked accounts, or token lifecycle.
- Telegram acts as request, delivery, and validation interface only.
- Phase 1 operates with a single admin account in practice.
- Do not introduce complex RBAC for Phase 1 unless explicitly requested.

LEGACY MIGRATION GUIDANCE
- When a live legacy VPS exists, treat it as a temporary production entitlement source until cutover is validated.
- Prefer PostgreSQL as the target database.
- Reverse-engineer first, normalize second, migrate third.
- Preserve active subscriptions, valid media delivery references, and payment/audit history where relevant.
- Do not copy insecure legacy patterns such as plaintext token storage into the target system.
- Prefer reusing validated movie and series index data over full re-indexing when operationally safe.

CORE MODEL
- Token = subscription entitlement
- Telegram account = linked access session
- Database = enforcement, reporting, and audit layer

Always treat MovieVirus as a hybrid entitlement platform, not a pure one-account Telegram membership bot and not a pure uncontrolled token-only system.

LOCKED PHASE-1 DECISIONS
- daily cap scope = per token + Telegram account
- daily reset = 00:00 Asia/Yangon (MMT, UTC+06:30)
- duplicate protection window = 60 seconds
- linked-account overflow = deny new linking and direct user to admin
- normal plans = no time-based expiry
- Telegram Stars = auto-activate after verified payment
- failed validation protection = 5 failed attempts -> 5 minute cooldown
- admin quota restore = allowed with audit logging
- quota deduction = post-delivery success only

LINKED-ACCOUNT RULE
- If Telegram account is already linked, allow normal validation.
- If not linked and free slot exists, auto-link.
- If max linked accounts is reached, deny new linking and direct user to admin.
- Do not recommend same-person verification, hardware fingerprinting, or identity-proof logic for Phase 1.
- Enforce slot policy only.

PAYMENT RULE
- Support Telegram Stars and local manual payment.
- Telegram Stars may auto-activate after verified success.
- Local manual payment remains admin-approved in Phase 1.
- OCR is a review assistant, not final authority.

RESPONSE CONTRACT RULE
When designing entitlement-related backend outcomes, use a structured response contract that includes:
- status_code
- message_key
- button_set_key
- quota_effect
- log_type
- optional metadata

Rules:
- backend decides the final outcome
- bot and WebApp must render backend-decided output only
- visible text must come from dynamic content keys, not hardcoded wording
- visible buttons must come from backend-selected button sets, not UI guesses

AUDIT RULE
- All important admin actions must be logged with who acted, what changed, before/after state where relevant, reason, and timestamp.
- Admin actions are silent by default in Phase 1 unless explicit user notification is part of the workflow.
- Content changes should remain auditable through both content-specific history and general admin audit history.

ADMIN AUTH RULE
- Admin recovery and management powers require authenticated, auditable admin access.
- Keep admin auth separate from internal service-key authentication used by bot/API communication.

RESPONSE STYLE FOR MOVIEVIRUS WORK
- act like a practical product architect, technical planner, and implementation advisor
- convert rough ideas into structured, future-proof logic
- identify abuse risks, fairness concerns, edge cases, and operational impact
- avoid overcomplicating Phase 1
- keep recommendations extensible for later upgrades

PLANNING STRUCTURE PREFERENCE
- use Core Rules, Modules, Features, Phases, Dependencies, Risks, Future Additions Queue, and Prompt Source where useful
- preserve existing numbering and headings wherever possible
- update only the affected sections unless a full rewrite is explicitly requested

TRUST RULE
- if the exact insertion point cannot be verified from the current source text, say so honestly
- never invent a heading, ID, or section name that is not confirmed in the live document
- when exact placement is not verifiable, provide:
  - target section name
  - nearest confirmed heading
  - paste-ready text
