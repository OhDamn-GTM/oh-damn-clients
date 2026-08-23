# Pipeline management

Pipeline stages, SLAs, and handoffs.

Key open items (see [../hubspot-config.md](../CRM%20setup%20%26%20hygiene/hubspot-config.md), [../decisions-log.md](../decisions-log.md)):
- 7 pipelines found (incl. 3 near-duplicate exhibition pipelines) — 87% of deals stale, 69% no value, 0 closed won ever. Max 3 pipelines recommended: Main Sales, CPD/Specification, Technical Testing (audit recommendation, pending Robert's sign-off).
- **TF04** (pipeline consolidation — 3 exhibition pipelines → Main Sales Pipeline): built, in sales-team trial. Do not touch the test pipeline.
- **TF10** (regional routing workflow): built, not live — was blocked on territory sign-off, now unblocked (Territory V1.1 signed off, including Scotland & Borders postcode rename).
- Meeting types (Site Visit, Survey, Follow-up, CPD) handled as meeting-type config on the deal, not new pipeline stages — agreed to avoid deals getting stuck "between two stages."
- Sector/industry dropdown will mirror the Firefly website case-study categories rather than a generic HubSpot industry list.
