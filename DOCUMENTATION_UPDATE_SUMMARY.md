# Documentation Update Summary - Token Regeneration Framework

## Date: 2026-04-06

## Overview
Updated both master-instruction-source.md and master-implementation-plan.md to reflect the new token regeneration and pre-launch reset framework.

## Changes Made

### master-instruction-source.md (v1.3.0 → v1.3.1)

1. **Version Block (A.2)** - Updated to 1.3.1, dated 2026-04-06

2. **Changelog Entry (A.4.18)** - Added new entry documenting:
   - Pre-launch legacy-token replacement with fresh-token reset policy
   - Global token regeneration as revoke-and-recreate with no carry-over
   - Admin-selectable token regeneration modes
   - Encrypted plaintext retention in tokens table only
   - Removal of legacy-token UI/fallback dependencies

3. **Token Model (B.2)** - Expanded to include:
   - tokens table as single source of truth
   - Encrypted plaintext storage rules
   - Masked preview as default
   - Pre-launch reset rules
   - New-user default token generation
   - Admin override for custom tokens

4. **Token Security (D.5.1)** - Enhanced with:
   - Encrypted plaintext retention only in tokens table
   - Never log plaintext tokens
   - Never store plaintext in linked_accounts
   - Explicit reveal with audit logging
   - Regeneration creates new token value

5. **Recovery Security (D.5.3)** - Added:
   - Admin-triggered token regeneration
   - Selectable regeneration modes
   - Detailed regeneration options (preserve/reset state, links, entitlements)
   - Pre-launch bulk reset capability

6. **Admin Approval and Restore Rule (D.9.3.1)** - Added capabilities:
   - Create fresh tokens
   - Regenerate/reissue tokens for leak response
   - Trigger pre-launch bulk token reset
   - Detailed audit requirements for bulk operations

7. **Token Control Rule (D.9.3.4)** - Enhanced with:
   - Regenerate token capability
   - Create replacement with preserved/fresh state
   - Revoke-and-replace mode rules
   - State preservation options

### master-implementation-plan.md (v1.1.0 → v1.1.1)

1. **Version Block (A.2)** - Updated to 1.1.1, dated 2026-04-06

2. **Changelog Entry (A.3.33)** - Added new entry documenting:
   - Legacy token replacement with revoke-and-recreate
   - Global fresh-token migration planning
   - Admin-selectable regeneration modes
   - Encrypted plaintext retention clarification
   - Legacy-token UI removal planning

3. **Usage Logic (B.3.3)** - Added rules:
   - Token regeneration doesn't consume quota
   - Linked-account reset during regeneration doesn't consume quota
   - Pre-launch reset creates fresh quota state

4. **Token Security (C.5.1)** - Enhanced with:
   - Encrypted plaintext retention only in tokens table
   - Never log plaintext tokens
   - Never store plaintext in linked_accounts
   - Explicit admin reveal with audit
   - Regeneration creates new token value

5. **Recovery Security (C.5.3)** - Added detailed modes:
   - Revoke old + create new
   - Preserve entitlement state
   - Preserve/reset linked accounts
   - Fresh entitlement with custom allowances
   - Global pre-launch migration/reset

6. **Token Management (C.9.2)** - Expanded with:
   - Regenerate token capability
   - Create custom tokens with special allowances
   - Pre-launch global reset capability
   - Detailed selectable regeneration options
   - tokens table as single source of truth

7. **Tokens Management Screen (C.9.9)** - Added features:
   - Regenerate token action
   - Reveal token through explicit privileged action
   - Copy token for controlled re-delivery
   - Choose regeneration mode from UI
   - Pre-launch global reset from protected admin flow
   - Regeneration history tracking
   - Legacy-token fallback removal notes

8. **Members Screen (C.9.10)** - Added capabilities:
   - Create fresh token for member
   - Regenerate current token for member
   - Choose preservation vs fresh state
   - Jump to token detail safely
   - Same backend regeneration policy as token view

## Key Principles Established

1. **Single Source of Truth**: tokens table is the only place for token plaintext encryption storage
2. **Security First**: Plaintext tokens never logged, never stored in linked_accounts
3. **Explicit Reveal**: Token reveal requires explicit admin action with audit logging
4. **Flexible Regeneration**: Multiple regeneration modes for different support scenarios
5. **Pre-launch Reset**: Capability to globally reset tokens before official launch
6. **Fresh State Option**: Ability to start users as completely fresh with no carried state

## Files Modified
- `/home/runner/work/movievirus-docs/movievirus-docs/master-instruction-source.md`
- `/home/runner/work/movievirus-docs/movievirus-docs/master-implementation-plan.md`

## Verification
All required sections have been successfully updated with the new token regeneration framework specifications. The documentation now provides clear guidance for implementing:
- Backend token regeneration framework
- Global pre-launch token reset/migration
- Admin web UI updates
- Legacy token UI cleanup
- Runtime verification requirements
