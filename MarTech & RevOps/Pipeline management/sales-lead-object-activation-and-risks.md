# Sales Lead Object Activation and Risks (A7)

## Current closed-lost data situation

Sales Pipeline has 731 deals total, 586 (80.2%) Closed Lost. That headline number is misleading — 520 of those 586 (89%) were closed via three bulk-administrative cleanup operations, not a real sales process:

- 442 deals closed simultaneously at 2026-04-21 14:26, reason "No Engagement"
- 56 closed simultaneously at 2026-03-18 14:32, reason "No Reply"
- 22 closed across a few timestamps in August 2026, labeled "Old Deal"

Most are single company-name records (football clubs, security firms, universities) created in dense clusters seconds apart back in 2022–2023 — consistent with a cold prospecting list bulk-imported directly as Deals rather than entering as qualified Leads.

Only 66 of 586 Closed Lost deals (11%) carry individualized, sales-process-driven reasons (lost tender, chosen competitor, poor product fit, etc.) — **that's the genuine closed-lost figure.** Partnerships pipeline (173 deals, post-sale/renewal) is a separate, much healthier picture.

## What activating the Leads object involves, and the risk

Portal is on Sales Hub Professional (6/6 Sales Seats, currently full) — meets HubSpot's minimum requirement for Leads object.

**What it involves:** Leads can't exist standalone — each must attach to a Contact or Company. Implementation means defining lead stages and qualification criteria, rebuilding lead-routing/assignment logic, and redirecting current deal-creation triggers (forms, workflows) so they create a Lead first, with Deal creation gated behind qualification.

**Risk to existing data:** the 731 historical Sales Pipeline deals, including the 520 bulk-closed legacy records, will remain as-is.

**Additional constraint:** a Sales seat is required to create Leads from the contacts index page or sales workspace — the primary day-to-day paths reps would use. All 6 seats are currently in use, so some team members may need a freed-up or additional seat.

**Transition risks to plan for:**
- Workflows tied to old deal-creation triggers may leave records stuck between stages if not resequenced carefully.
- Running both intake paths in parallel (old deal-creation and new lead-creation) risks duplicate Contact/Company/Deal records if not deduplicated.
- Existing reports/dashboards built on deal-stage data will need rebuilding or extending to reflect the new Lead stage.

## Recommendation before any pipeline changes

**Activate the Leads object** — it directly addresses the root cause (unqualified prospects entering as full Deals, producing an 89%-inflated closed-lost figure). Treat as phased implementation, not a switch flip:

- HubSpot tier is already sufficient — no procurement delay.
- Define lead stages and qualification criteria, pilot on a subset of new leads before full rollout.
- Resequence existing deal-creation workflows deliberately rather than disabling outright.
- Regardless of Leads object timeline: **exclude/archive the 520 bulk-closed legacy deals from any going-forward closed-lost rate calculations** — mixing them with real losses makes every historical comparison meaningless.
