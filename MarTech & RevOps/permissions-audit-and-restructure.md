# HubSpot Permission Audit and Restructure (A10)

## Why this matters

The portal currently has 8 users with full Super Admin access — nearly a third of active users. This audits every current user, flags Super Admin holders, and proposes a leaner structure: one named central admin, one backup, everyone else on role-scoped permission sets.

## Portal snapshot

- 27 user records: 17 active, 10 deactivated (37% of all records are stale accounts still in the portal).
- 8 users hold Super Admin: 4 internal Halo staff, 1 deactivated internal account, 3 external users at Bound.
- Users span 8 email domains, including freelance devs/design agencies (codecaste.com, zimcode.com, pebbledesigns.co.uk / goldpebble.co.uk, hardyaccounting.com). Several already deactivated — worth confirming none still need standing access.

## Everyone with Super Admin access today

| Name | Email | Status | Team |
| --- | --- | --- | --- |
| Caitlin Leatham | caitlin@halosolutions.com | Active | Operations |
| Ali Bott | ali@halosolutions.com | Active | Approver |
| Lloyd Major | lloyd@halosolutions.com | Active | Operations |
| Chloe Fox | chloe@halosolutions.com | Active | Marketing |
| Thomas Rickard | tom@halosolutions.com | Deactivated (10mo inactive) | Tech |
| Rui Calvario | rui@boundm.com | Active, external partner (Bound) | Partner seat |
| Alicia Elston | alicia@boundm.com | Active, external partner (Bound) | Partner seat |
| James Cook | james@boundm.com | Active, external partner (Bound) | Marketing / Partner seat |

### Risk notes

- Thomas Rickard: deactivated but still carries Super Admin — leftover with no benefit, safe to remove immediately.
- 3 of 8 Super Admins (Rui Calvario, Alicia Elston, James Cook) are external users at Bound.
- 4 active internal staff (Caitlin, Lloyd, Chloe, Ali) hold Super Admin — best practice is 1 primary + 1 backup; everyone else should move to a permission set matching their actual job.

## Recommended structure

**Central Admin (Super Admin): Caitlin Leatham** — Operations/Tech (natural home for admin), logs in daily, 2FA enabled, paid full seat, already holds Super Admin — no new provisioning needed, just remove the redundant admins around her.

**Secondary / Emergency Admin (Super Admin): Ali Bott** — already the approving stakeholder, active daily, 2FA enabled. Second admin means the portal is never one absence away from unmanageable.

Everyone else (Lloyd Major, Chloe Fox, and the 3 Bound users) moves to a role-scoped permission set mirroring actual day-to-day use.

## Secondary observations

7 active users hold "User table access" (view/manage user list) without being full Super Admins:

| Name | Email | Team | Elevated permission | Note |
| --- | --- | --- | --- | --- |
| Isabelle Halliday | isabelle@halosolutions.com | Tech Team | User table access | No 2FA |
| James Spencer | james@halosolutions.com | Partnerships Team | User table access | |
| Lois Warner | lois@halosolutions.com | Sales Team | User table access | |
| Bryan Huneycutt | bryan@halosolutions.com | Sales Team | User table access, Users write | |
| Charlie Archer | charlie@halosolutions.com | Partnerships Team | User table access | |
| Grace Hardy | g.hardy@hardyaccounting.com | None (external) | User table access | |
| Taran Stafford | dean.hodges@pebbledesigns.co.uk | None (external) | User table access | |

10 of 27 accounts are deactivated but still present, including a generic "System Admin" (itadmin@halosolutions.com) account already deactivated — a periodic cleanup pass would fully offboard stale records.

## Rollout plan (sequenced to avoid disruption/lockout)

**Phase 1 — immediate, zero risk**
Remove Super Admin from Thomas Rickard (already deactivated, 10mo inactive). No live user affected.

**Phase 2 — after Ali's sign-off**
- Confirm Caitlin (central) and Ali (secondary) keep Super Admin.
- Move Lloyd Major and Chloe Fox to a permission set mirroring their current functional access minus Super Admin — verify each can still do normal work immediately after.
- Confirm with Bound what their active engagement actually requires, then scope Rui, Alicia, James (Bound) access.

**Phase 3 — safety net**
- Keep both Caitlin and Ali as Super Admin throughout the transition so there's always an admin who can immediately reverse a breaking change.
- Re-check in 30 days that nobody lost needed access; set a recurring quarterly permissions review going forward so the count doesn't creep back up.
