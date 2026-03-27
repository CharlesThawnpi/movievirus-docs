# MovieVirus Master Implementation Plan

## Header
- Project: MovieVirus
- Document Type: Master Implementation Plan
- Purpose: Single source of truth for future implementation planning, module-by-module build design, phase-by-phase rollout, and VS Code prompt generation
- Status: Active Planning Draft
- Owner: Charles

---

## Version Block
- Version: 1.0.0
- Last Updated: 2026-03-27
- Update Method: Section-based manual update
- Update Rule: Prefer updating only the affected phase, module, feature, dependency, risk, queue item, or prompt source instead of regenerating the whole document

---

## Change Log

### CHG-001 | 2026-03-27
- Initial Master Implementation Plan created
- Added planning rules, scope, business model, modules, phases, dependencies, risks, future additions queue, and prompt source sections
- Established stable IDs for future modular updates
### CHG-002 | 2026-03-27
- Added PostgreSQL as recommended VPS-2 target database
- Added legacy VPS-1 to VPS-2 migration planning logic
- Added database normalization, entitlement carry-over, and media index reuse guidance
- Added migration-related phases, dependencies, risks, and prompt-source rules

---

## Update Protocol
Use this document as the implementation planning source. Future updates should follow these rules:

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

### Example update requests
- Update only Change Log + Module 10
- Insert new feature as M07-F05
- Add new dependency as DEP-04
- Add Phase 03 payment implementation details
- Rewrite only Prompt Source for Module 06
- Move Q-004 into Module 08
- Generate VS Code prompt for Phase 01 only

---

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

---

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

### Out of Scope for Initial Build
- advanced anti-abuse scoring
- full automatic OCR payment approval
- complex family plan billing logic
- heavy analytics dashboards
- advanced content recommendation engine
- hardware fingerprinting
- commercial-grade identity verification

---

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

### BL-07. Legacy Migration Logic
For VPS-1 to VPS-2 transition:
- PostgreSQL is the recommended target database for VPS-2
- legacy SQLite data should be treated as source input, not as the target schema design
- active subscriptions must remain valid through their carried-over entitlement period
- valid media index data should be reused when delivery references remain operational
- expired or already used short-lived delivery tokens should not be migrated as active target tokens
- insecure legacy storage patterns must be removed during migration
---

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

---

## Module 03. Linked Accounts / Device Slots

### M03-F01. Linked Account Logic
- linked account reuse
- auto-link if slot available
- deny if no slot and no allowed replacement path

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

### M07-F03. OCR Rule
Use OCR as review assistance, not full auto-approval in phase 1.

### M07-F04. Payment Statuses
- Pending
- OCR Matched
- OCR Uncertain
- Approved
- Rejected
- Refunded
- Expired Pending

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

## Module 13. Legacy Migration and Cutover

### M13-F01. Migration Objective
Safely migrate VPS-1 legacy data and active users into VPS-2 without breaking entitlement continuity, delivery integrity, or auditability.

### M13-F02. Target Database Rule
Use PostgreSQL as the VPS-2 target database. Do not reuse the legacy SQLite schema directly as the production target design.

### M13-F03. Source-to-Target Mapping
Recommended mapping:
- users -> members
- daily_usage -> member_daily_usage
- transactions -> payments
- delivery_tokens -> access_tokens plus access_token_items when batch payload normalization is required
- movies and series -> media_assets or retained split media tables depending on final schema decision
- series_episode_map -> media_episode_map
- request_events / search_miss / ai_events -> analytics tables

### M13-F04. Data Classification Rule
Classify legacy data before import:
- MUST migrate: active member entitlement data, payment history, daily usage baselines where relevant, movies, series, episode mapping, core media references
- SHOULD migrate: analytics and reminder history where useful
- DISCARD or REBUILD: expired/used short-lived delivery tokens, stale request placeholders, obsolete cleanup queues, invalid orphan rows

### M13-F05. Normalization Rule
Before import:
- recompute member status from dates instead of trusting legacy status blindly
- preserve original legacy IDs in mapping columns
- normalize CSV batch payloads into child rows
- clean orphan rows
- normalize enums and plan references
- enforce target-side foreign keys and indexes

### M13-F06. Delivery Integrity Rule
Validate inherited Telegram delivery references before cutover. If delivery depends on source chat/message mapping, sample verification is mandatory before decommissioning VPS-1.

### M13-F07. Cutover Rule
Migration should use:
- immutable backup
- staging cleanup
- validation import
- final delta sync
- cutover switch
- rollback-safe read-only window for VPS-1

### M13-F08. Security Remediation Rule
VPS-2 must remove insecure legacy practices such as:
- plaintext token storage
- publicly exposed dev admin services
- missing relational integrity
- weak audit preservation
---

[M00-LM Legacy Migration & Cutover Module — ADD]

Module ID: M00-LM
Title: Legacy VPS Discovery, Data Reuse, Migration Normalization, and Cutover

Purpose
Enable safe transition from VPS-1 to VPS-2 while preserving active member entitlements, reusing the existing media index, and removing legacy schema/security weaknesses.

Scope
- reverse-engineer VPS-1 production logic
- migrate active subscription state
- reuse movies/series index data
- normalize legacy database structure
- validate Telegram delivery integrity
- execute rollback-safe cutover
- decommission VPS-1 only after parity confirmation

Business Logic Impact
- active users on VPS-1 remain entitled through their existing expiry dates
- downgrade/upgrade policy for the new system does not retroactively remove legacy entitlements during migration
- old short-lived delivery tokens are not business-critical and should not be migrated as active tokens
- daily usage carry-over may be migrated when fairness requires same-day enforcement continuity
- legacy plan names may be preserved as mapped plan aliases until renewal converts users onto VPS-2-native plans

Workflow Impact
- discovery precedes schema design finalization for migration-affected entities
- migration runs through staging validation before production cutover
- cutover includes write freeze, import, validation, switch, rollback window
- file delivery on VPS-2 must be validated using inherited Telegram source message references before VPS-1 shutdown

Database Impact
Source audit indicates VPS-1 production currently uses:
- SQLite database
- users
- daily_usage
- transactions
- delivery_tokens
- movies
- series
- series_episode_map
- request_events
- search_miss
- ai_events
- message_delete_queue
- expiry_reminders

Recommended target mapping
- users -> members
- daily_usage -> member_daily_usage
- transactions -> payments
- delivery_tokens -> access_tokens plus access_token_items
- movies + series -> media_assets or retained split structure
- series_episode_map -> media_episode_map
- request_events / search_miss / ai_events -> analytics tables
- requests / message_delete_queue -> ephemeral ops tables only if still needed

Normalization Rules
LM-R01. Recompute membership status from authoritative dates during import instead of trusting legacy status blindly.
LM-R02. Preserve original legacy IDs in migration reference columns for traceability.
LM-R03. Convert plaintext or short-lived token patterns into hashed-at-rest target rules; expired/used delivery tokens should normally not migrate.
LM-R04. Split any CSV batch media payloads into normalized child rows.
LM-R05. Enforce FK constraints in VPS-2 after staging cleanup.
LM-R06. Enforce uniqueness on media identity using file_unique_id where available.
LM-R07. Flag rows with missing file_unique_id or incomplete episode mapping for remediation queue instead of silent discard.
LM-R08. Preserve payment history and admin-review evidence fields where available.
LM-R09. Preserve language preference where present.
LM-R10. Store migration audit metadata for every imported member/payment/media row.

Security Remediation Requirements
LM-S01. Remove plaintext secret exposure from legacy deployment pattern.
LM-S02. Replace public Flask dev-admin exposure with secured admin interface or private admin gateway.
LM-S03. Eliminate plaintext token-at-rest behavior in VPS-2.
LM-S04. Add integrity constraints to prevent new orphan rows.
LM-S05. Log all migration admin actions and cutover checkpoints.

Admin Impact
- admin needs migration dashboard or runbook visibility for:
  - import counts
  - rejected rows
  - orphan cleanup summary
  - media integrity verification results
  - entitlement parity checks
- admin must be able to manually resolve:
  - unmapped plans
  - broken file references
  - stale pending payments
  - member status anomalies

User Impact
- active members should experience continuity without forced repurchase
- existing expiry dates should remain honored
- users may be silently migrated where possible, but major user-facing changes should be minimized during cutover
- denial reasons on VPS-2 must remain explicit if migrated records are incomplete or suspended

Payment Impact
- preserve completed and relevant pending payment history for audit
- stale unresolved pending payment records from legacy system should be tagged for admin review, not auto-approved
- legacy OCR/admin-review metadata should migrate if it supports dispute handling

Reporting / Audit Impact
- maintain migration log tables:
  - migration_runs
  - migration_row_audit
  - migration_rejections
  - cutover_checkpoints
- preserve old-to-new ID mapping for members, payments, and media rows
- store snapshot totals and validation checksums for cutover evidence

New Features
M00-LM-F01. VPS-1 schema discovery and compatibility audit
M00-LM-F02. Legacy-to-target mapping dictionary
M00-LM-F03. Staging import pipeline
M00-LM-F04. Data cleanup and orphan handling rules
M00-LM-F05. Active subscription carry-over logic
M00-LM-F06. Legacy plan alias support
M00-LM-F07. Media index reuse and delivery-reference validation
M00-LM-F08. Cutover freeze and rollback procedure
M00-LM-F09. Post-cutover parity verification
M00-LM-F10. Legacy shutdown checklist

Recommended Phase Additions
PH-LM-01 Discovery
- confirm source schema, runtime stack, service layout, token logic, and delivery model
- capture immutable backups
- classify tables into must/should/discard

PH-LM-02 Staging Normalization
- cleanse orphans
- normalize enums and plan values
- split batch token payloads
- prepare ID mapping tables
- verify source message reference quality

PH-LM-03 Import to VPS-2
- load members, usage baselines, payments, media index, analytics as planned
- enforce target-side validation and rejection logging
- recompute derived fields

PH-LM-04 Delivery Verification
- sample-check movie and series delivery using inherited file_chat_id/message_id references
- verify subscription enforcement and daily-cap behavior
- verify payment/admin views for migrated rows

PH-LM-05 Cutover
- temporary freeze on VPS-1 writes
- final delta export/import
- switch bot traffic and webhooks
- enable heightened logging

PH-LM-06 Rollback Window and Decommission
- keep VPS-1 read-only for defined rollback period
- monitor entitlement, payment, and delivery parity
- decommission only after parity signoff

Dependencies
DEP-LM-01. Backups of media.db, bot code, env/config, and systemd service definitions
DEP-LM-02. Final VPS-2 target schema decision for media model (unified vs split)
DEP-LM-03. Plan-alias mapping between legacy plans and VPS-2 plans
DEP-LM-04. Telegram delivery validation environment
DEP-LM-05. Migration audit logging tables in VPS-2
DEP-LM-06. Admin review process for rejected or ambiguous rows

Risks
RSK-LM-01. Active entitlement loss if status/date mapping is wrong
RSK-LM-02. Delivery failure if inherited message references are invalid or channel access differs on VPS-2
RSK-LM-03. Data integrity issues from legacy orphan rows and weak typing
RSK-LM-04. Security carry-over if plaintext secrets/tokens patterns are copied forward
RSK-LM-05. Payment disputes if stale pending transactions are mishandled
RSK-LM-06. Search gaps if media dedupe or merge logic incorrectly collapses distinct entries
RSK-LM-07. Series availability mismatch due to incomplete episode mapping in legacy data

Future Additions Queue
Q-LM-001. Automated migration dry-run checker
Q-LM-002. Media reference health scanner
Q-LM-003. Legacy plan retirement workflow on renewal
Q-LM-004. Self-service member migration status checks
Q-LM-005. Post-migration analytics parity dashboard

Prompt Source Add
Use VPS-1 audit findings as authoritative migration input:
- Ubuntu 22.04.1 LTS
- Python 3.10
- python-telegram-bot
- aiosqlite
- SQLite media.db
- delivery via copy_message using file_chat_id + file_message_id
- active subscriptions and legacy plans preserved through migration
- movies and series index reuse preferred over re-indexing
- old short-lived delivery tokens should not drive target design

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
- inspect VPS-1 schema and logic
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
- switch traffic to VPS-2
- maintain rollback-safe VPS-1 read-only window

Modules:
- M13
- part of M02
- part of M06
- part of M09
- part of M10
---

Recommended Phase Additions
PH-LM-01 Discovery
- confirm source schema, runtime stack, service layout, token logic, and delivery model
- capture immutable backups
- classify tables into must/should/discard

PH-LM-02 Staging Normalization
- cleanse orphans
- normalize enums and plan values
- split batch token payloads
- prepare ID mapping tables
- verify source message reference quality

PH-LM-03 Import to VPS-2
- load members, usage baselines, payments, media index, analytics as planned
- enforce target-side validation and rejection logging
- recompute derived fields

PH-LM-04 Delivery Verification
- sample-check movie and series delivery using inherited file_chat_id/message_id references
- verify subscription enforcement and daily-cap behavior
- verify payment/admin views for migrated rows

PH-LM-05 Cutover
- temporary freeze on VPS-1 writes
- final delta export/import
- switch bot traffic and webhooks
- enable heightened logging

PH-LM-06 Rollback Window and Decommission
- keep VPS-1 read-only for defined rollback period
- monitor entitlement, payment, and delivery parity
- decommission only after parity signoff


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

DEP-LM-01. Backups of media.db, bot code, env/config, and systemd service definitions
DEP-LM-02. Final VPS-2 target schema decision for media model (unified vs split)
DEP-LM-03. Plan-alias mapping between legacy plans and VPS-2 plans
DEP-LM-04. Telegram delivery validation environment
DEP-LM-05. Migration audit logging tables in VPS-2
DEP-LM-06. Admin review process for rejected or ambiguous rows

### DEP-06. Legacy Data Backup Set
Required before migration work begins. Must include legacy SQLite DB, code snapshot, env/config snapshot, and service definitions.

### DEP-07. PostgreSQL Target Schema
Required before staging import, mapping validation, and constraint enforcement.

### DEP-08. Legacy-to-Target Mapping Rules
Required before member, payment, media, and analytics import logic can be finalized.

### DEP-09. Delivery Reference Validation
Required before cutover to confirm inherited Telegram source references remain usable on VPS-2.
---

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

RSK-LM-01. Active entitlement loss if status/date mapping is wrong
RSK-LM-02. Delivery failure if inherited message references are invalid or channel access differs on VPS-2
RSK-LM-03. Data integrity issues from legacy orphan rows and weak typing
RSK-LM-04. Security carry-over if plaintext secrets/tokens patterns are copied forward
RSK-LM-05. Payment disputes if stale pending transactions are mishandled
RSK-LM-06. Search gaps if media dedupe or merge logic incorrectly collapses distinct entries
RSK-LM-07. Series availability mismatch due to incomplete episode mapping in legacy data

### RSK-05. Entitlement Carry-Over Risk
Risk:
- active members may lose time, quota continuity, or status accuracy during migration
Mitigation:
- recompute entitlement from authoritative dates
- preserve legacy references
- validate active user samples before cutover

### RSK-06. Delivery Reference Risk
Risk:
- inherited Telegram message references may fail on VPS-2 if channel access or message integrity differs
Mitigation:
- sample delivery validation
- fallback remediation queue
- do not decommission VPS-1 before parity confirmation

### RSK-07. Legacy Security Debt Risk
Risk:
- insecure legacy patterns may be copied into VPS-2
Mitigation:
- PostgreSQL target redesign
- hashed token storage
- FK enforcement
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
---

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

Future Additions Queue
Q-LM-001. Automated migration dry-run checker
Q-LM-002. Media reference health scanner
Q-LM-003. Legacy plan retirement workflow on renewal
Q-LM-004. Self-service member migration status checks
Q-LM-005. Post-migration analytics parity dashboard

### Q-007. Migration Dry-Run Checker
Potential later enhancement for repeatable pre-cutover validation.

### Q-008. Media Reference Health Scanner
Potential later enhancement for checking inherited Telegram delivery references at scale.

### Q-009. Legacy Plan Retirement Workflow
Potential later enhancement for converting legacy carried-over users into fully native VPS-2 plan structures on renewal.
---

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

### Migration Prompt Source Add
When generating migration or database prompts:
- treat VPS-1 SQLite as source only
- target PostgreSQL for VPS-2
- preserve active member entitlements
- preserve payment and audit history where relevant
- validate inherited Telegram media delivery references
- normalize and clean legacy rows before production import
---

Prompt Source Add
Use VPS-1 audit findings as authoritative migration input:
- Ubuntu 22.04.1 LTS
- Python 3.10
- python-telegram-bot
- aiosqlite
- SQLite media.db
- delivery via copy_message using file_chat_id + file_message_id
- active subscriptions and legacy plans preserved through migration
- movies and series index reuse preferred over re-indexing
- old short-lived delivery tokens should not drive target design


## Current Implementation Focus
- planning only
- PostgreSQL target schema for VPS-2
- legacy VPS-1 to VPS-2 migration design
- refine modules and phases first
- keep future build prompts consistent with this document

---

## Final Planning Note
This document is the adjustable implementation blueprint for MovieVirus. It should be updated feature by feature, module by module, phase by phase, and section by section as the product definition becomes more mature.
