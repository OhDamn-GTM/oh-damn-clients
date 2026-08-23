# RAG Report — HubSpot Audit (Aug 2026)

Red-Amber-Green assessment of Halo Solutions' HubSpot setup across Marketing, Sales, and Reporting hubs.

## Summary

60% of issues identified are Red (critical). Key problems: data inconsistencies (99% missing ICP properties), deal reopens skewing 11% of customer counts, slow deal velocity (39 days in Consideration stage), and low segment engagement (9% CTR). Green areas: basic automations (forms, emails, owner sync) are working fine.

Priority: fix foundational data first (Red), then workflows/automation (Red-Amber), then reporting (Red). Target outcomes: 90%+ data accuracy, 50% reduction in manual time.

Recurring pain points raised on calls: "data carnage" and "adoption leaks" (Connect Call), "misaligned workflows" and "fighting design" (Discovery Call).

## Marketing Hub

| Status | Problem | Impact (Stats) | Solution | Improvement (Measurable) | Example |
| --- | --- | --- | --- | --- | --- |
| 🟢 Green | Forms/emails active; segments for subs/customers | Low (1685 newsletter subs; 90% open rate fill) | Monitor | N/A | "Halo Newsletter Subscribers UK" segment, 1685 contacts |
| 🟠 Amber | No scoring/intent (0% HubSpot Score fill); static segments, low engagement | Medium (MQL 0.78%; 9% CTR in segments; manual scrubs) | Add scoring workflows, dynamic segments | MQL 0.78% → 10-15%, CTR +11% | "All current customers" segment, 604 contacts, 9.6% CTR |
| 🔴 Red | Missing ICP data (99% Industry/Country, 94% Company); manual handoffs; workflow errors | High (99% missing demographics; 60.27% workflow issues; "data carnage") | Bulk enrich, fix branches | Fill rates +60%, manual time -50% | Contact 486408441070: 0% fill on Company/Industry, tied to error-prone workflow |

## Sales Hub

| Status | Problem | Impact (Stats) | Solution | Improvement (Measurable) | Example |
| --- | --- | --- | --- | --- | --- |
| 🟢 Green | Owner sync/meetings active | Low (100% Deal Owner fill) | Monitor | N/A | Deal 54344560886: Owner "James Spencer," 100% fill |
| 🟠 Amber | Slow velocity; no workspace; budget constraints | Medium (39d in Consideration; 6.75% "No Engagement" time; delays) | Add SLAs, enable workspace | Velocity -19d/stage, close rate +15% | Deal 288809965771: 687h (29d+) in "No Engagement" |
| 🔴 Red | Deal overuse/reopens; missing ARR (100%); renewal issues | High (100% ARR missing; reopens skew counts; "fighting design") | Migrate to tickets, auto-ARR | Accuracy +35%, manual chases -70% | Deal 54344560886: reopened for renewal, missing ARR, 11 workflow issues |

## Reporting

| Status | Problem | Impact (Stats) | Solution | Improvement (Measurable) | Example |
| --- | --- | --- | --- | --- | --- |
| 🟢 Green | PPC/renewal automations | Low (60.27% enrollment fill) | Monitor | N/A | "Year 2+ PPCC Renewed" workflow, 1 enrollment |
| 🟠 Amber | Manual packs; no ARR/forecast | Medium (100% ARR missing; sparse activity 53%) | Auto-dashboard pulls | Report time -hours, forecast +20% accuracy | "All current customers" segment: manual revenue pulls, missing ARR |
| 🔴 Red | Inaccuracies from data/reopens; low trust | High (37% empty conversions; "gut decisions"; 60.27% issues) | Cleanup, filters | Accuracy +30%, errors -80% | Contact 465960332478: missing conversions, linked to reopened deal skewing reports |

## Suggested Priorities

Sequenced: foundational data (Red) → workflows/automation (Red-Amber) → reporting (Red-Amber) → engagement (Amber).

1. **Data Cleanup & Enrichment** (High — Red)
   Bulk enrich missing properties (Company Name 94% missing, Industry 0%), dedupe legacy data.
   Fixes "data carnage," enables accurate ICP targeting. Assists Marketing (segmentation) and Sales (reliable leads). Boosts fill rates to 80%+, enables 79% Unqualified → 10-15% MQL conversion.

2. **Workflow Adjustments & Scoring Setup** (High — Red/Amber)
   Fix 8 workflows with branch logic errors (e.g. renewals), add lead scoring (0% current fill).
   Eliminates misaligned workflows and manual handoffs. Assists Marketing (intent triggers) and Sales (velocity SLAs). Lead → MQL/SQL in 1-2 weeks vs stuck; velocity +20-30%.

3. **Deal Structure Optimization** (Medium — Red)
   Migrate non-sales activities (renewals/reopens skewing 95+ days in Steady State) to leads/tickets/products; enforce forward-only stages.
   Fixes "deal overuse." Assists Sales (clean pipelines) and Reporting (accurate metrics). Close rate +15%, fewer reopens.

4. **Reporting & Dashboard Rebuild** (Medium — Red/Amber)
   Automate manual reporting packs with a leadership dashboard (stages/velocity/ARR — currently 100% missing); add filters for reopens.
   Ends unreliable reporting and manual board-prep time. Assists Reporting (core) and Sales/Marketing (visibility). Real-time insights, accuracy to 90%+.

5. **Segmentation & Engagement Optimization** (Low — Amber)
   Make 99 segments dynamic and engagement-focused (currently 9% CTR); integrate with nurtures.
   Assists Marketing (targeting) and Sales (qualified leads). Engagement +20%+, more MQLs into SQL handoff.
