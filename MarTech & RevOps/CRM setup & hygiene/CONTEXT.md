# CRM setup & hygiene

CRM structure, data quality, and related processes.

Key open items (see [../rag-report-aug2026.md](../rag-report-aug2026.md) and [../phase-2-schedule-of-work.md](../phase-2-schedule-of-work.md)):
- 99% of contacts missing Industry/Country, 94% missing Company — top priority fix, bulk enrich + dedupe legacy data (A1-A4, Data Cleanup & Enrichment priority).
- ARR data is split across `hs_arr` (native) and a custom property with 49 genuine conflicts out of 107 deals — see [arr-property-consolidation.md](arr-property-consolidation.md) (A1).
- 6 renewal/expiry properties doing the same job — rationalize down to 3 (Current Contract Start Date, Halo Licence Expiry, Payment Renewal Date) — see [../renewal-and-expiry-property-rationalisation.md](../renewal-and-expiry-property-rationalisation.md) (A8).
- 8 Super Admins currently, nearly a third of active users — leaner structure proposed — see [../permissions-audit-and-restructure.md](../permissions-audit-and-restructure.md) (A10).
- 8 workflows have branch logic errors; 0% lead scoring fill — needs scoring workflows added (Workflow Adjustments & Scoring Setup priority).
