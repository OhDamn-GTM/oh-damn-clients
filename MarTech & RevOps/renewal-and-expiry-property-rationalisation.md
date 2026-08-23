# Renewal and Expiry Property Audit and Rationalisation (A8)

## Objective

Six deal properties currently track renewal/expiry information with overlapping purpose. Audit all six, confirm the three to keep, set out migration for the three being retired, flag dependencies before archiving anything.

## Property audit

Fill rates measured across 904 deals. "Used In" = everywhere HubSpot recognises the property as referenced (views, reports, workflows, property cards, data highlights, lists).

| Property | Field type | Fill rate | Used In | Recommendation |
| --- | --- | --- | --- | --- |
| Current Contract Start Date | Date picker | 17.59% (159/904) | 12 | **Keep** |
| Halo Licence Expiry (End of Contract) | Date picker | 16.81% (152/904) | 22 | **Keep** |
| Payment Renewal Date | Date picker | 16.81% (152/904) | 12 | **Keep** |
| Halo Start Date | Date picker | 13.5% (122/904) | 8 | Archive, migrate first |
| Client Joined Halo | Date picker | 10.73% (97/904) | 0 | Archive, migrate first |
| Auto-renewal | Single checkbox | 6.86% (62/904) | 6 | Archive, open question |

## Data completeness

None of the three properties to keep are close to fully populated — 159/904, 152/904, 152/904 respectively. Migrating what already exists closes some of the gap, but most deals will still lack renewal/expiry data even after migration, since source properties are similarly sparse. **The input process itself (how/when these dates get entered) needs separate work once consolidation is complete.**

## Migration plan and dependencies

**Halo Start Date → Current Contract Start Date**
Affects up to 122 deals (fewer once already-filled overlaps excluded). Cannot archive immediately — actively referenced by 4 live workflows (Post-Purchase Workflow Year 1, Year 2+ PPCC Multi-Year contract, Halo Start Date Sync company to Deal, Client Details Form Data Sync), 3 views (Contract Renewal, Partnerships Accounts (No Filter), Partnership Board Backup), and 1 static list (Year 1 workflow enrollment). All must be repointed before archiving.

**Client Joined Halo → Current Contract Start Date**
10.73% fill rate suggests same underlying data as Current Contract Start Date, but not yet confirmed — needs verifying with the Halo team before merging. No dependency risk (used in 0 places).

**Auto-renewal**
A checkbox, not a date — can't be copied directly into a date property. Need to confirm what it's meant to capture (likely: does the contract auto-renew) and whether that signal already exists in the kept properties or needs preserving separately. Used in 6 places: 5 views (Contract Renewal, Partnerships/Sales, Partnerships Accounts, Partnerships Accounts-v2, Partnerships Accounts (No Filter)) + Client Details Form Data Sync workflow (also live on Halo Start Date).

**Shared dependency** — Client Details Form Data Sync references both Halo Start Date and Auto-renewal; only needs updating once, but resolve before either is archived.

**Cross-task dependency: Partnerships Pipeline** — a significant share of usages across the three properties being archived are Partnerships-pipeline views (Contract Renewal, Partnerships Accounts, Partnerships Accounts-v2, Partnerships Accounts (No Filter), Partnerships/Sales, Partnership Board Backup). This overlaps with the separate Partnerships Pipeline Retirement task (A6) — check whether these views are already scheduled for retirement there before doing this work twice.

## Deal card views

Checked live on both Sales and Partnerships pipelines — **neither shows any of the six renewal/expiry properties today.** Visible fields: Deal owner, Last Contacted, Deal Type, Priority, Closed Lost Reason. The task's stated goal (team seeing renewal/expiry dates clearly) is not currently met at all, independent of the duplication problem. Requires adding Current Contract Start Date, Halo Licence Expiry, and Payment Renewal Date to the card for the first time.

## Recommendation

1. Confirm the three properties to keep with Ali.
2. Resolve two open questions before migrating: does Client Joined Halo do the same job as Current Contract Start Date; what does Auto-renewal need to capture/preserve.
3. Migrate Halo Start Date → Current Contract Start Date only after the 4 dependent workflows + other references are repointed.
4. Migrate Client Joined Halo → Current Contract Start Date once confirmed with the Halo team.
5. Resolve Auto-renewal question + shared workflow dependency, then archive.
6. Add the three kept properties to the deal card on both pipelines.
7. Archive Halo Start Date, Client Joined Halo, Auto-renewal only after Ali confirms and all dependencies clear.
8. Treat the data-entry process as a separate second piece of work post-consolidation.

## Sign-off required

- Ali: confirm the three properties to keep before archiving.
- Halo team: confirm whether Client Joined Halo and Current Contract Start Date do the same job.
- Confirm what Auto-renewal is meant to capture and whether that signal is preserved.
