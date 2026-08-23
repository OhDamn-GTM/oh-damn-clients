# ARR Property Consolidation (A1)

Raw data: [data/arr-mismatch-breakdown-105deal-export.xlsx](data/arr-mismatch-breakdown-105deal-export.xlsx)

## Objective

Establish HubSpot's native `hs_arr` (Annual Recurring Revenue) property as the single source of truth for ARR, calculated automatically from deal line items, and retire the custom "Annual Recurring Revenue (ARR)" property.

## Mismatch findings

105-deal export comparing `hs_arr` vs custom ARR (plus Amount and Amount in company currency):

| Category | Deals | Description |
| --- | --- | --- |
| Match | 40 | `hs_arr` and custom ARR agree — no action needed |
| Zero `hs_arr`, custom ARR filled | 16 | Line items present but not configured as recurring |
| Zero custom ARR, `hs_arr` filled | 0 | No deals in this category |
| Genuine conflict | 49 | Both populated but disagree — needs reconciling before cutover |

Cross-referencing against the 12 non-GBP (multi-currency) deals confirmed mismatches aren't a currency-conversion basis error — `hs_arr` consistently calculates in native deal currency. However, FX deals are disproportionately represented in the Genuine conflict category (8/12 = 66.7% vs 46.7% of deals overall) — currency exposure correlates with mismatch risk even though it isn't the mechanical cause.

Note: the 105-deal set is narrower than full migration scope — Section below (107 deals) also includes deals where `hs_arr` is entirely blank rather than zero.

## Historic data migration requirement

107 deals have the custom ARR property filled — this is the full migration scope. Of these: 40 already match `hs_arr` (no correction needed), 65 fall into "Zero hs_arr" or "Genuine conflict" (need reconciliation), ~2 sit outside the 105-deal comparison because `hs_arr` is truly blank. All 107 need to be accounted for before the custom property is archived.

## Dependencies to resolve first

**Multi-currency plan** — four currencies in use (GBP, USD, EUR, CAD). `Amount in company currency` is already converted, but `hs_arr` always calculates in native deal currency, not normalized. Open decision: should ARR also be currency-normalized for reporting, or intentionally stay native like `hs_arr` does today? **Pending Ali's decision.** Recommend confirming this before finalizing ARR migration, so deals aren't migrated twice.

**Line item billing frequency completeness** — `hs_arr` only calculates correctly if every line item has a recurring billing frequency. Two confirmed issues:
1. The entire Halo Event Licence product tier (all capacity bands) has `Billing frequency = One-time` at the product level in the Product Library — any deal using these won't calculate `hs_arr`.
2. More significant: at least one deal (Motiv Sports) shows a correctly-configured recurring product (Halo Multi Site Licence, Monthly) still added to the deal with billing frequency overridden to One-time at the line-item level. This means the issue isn't confined to the Product Library — it needs scoping across additional Zero-hs_arr deals for the same override pattern, and must be corrected before `hs_arr` is declared "live."

## Recommended implementation plan

Sequenced to avoid data loss and a period where neither property is reliable:

1. Fix the billing frequency gap at product level; audit line items across Zero-hs_arr and Genuine-conflict deals for the same one-time override.
2. Sample additional Zero-hs_arr deals to scope how widespread the line-item override is.
3. Confirm the multi-currency/FX approach with Ali.
4. Reconcile the 107 deals — correct underlying line items so `hs_arr` calculates correctly. Prioritise the 49 "genuine conflict" deals first (highest risk).
5. Spot-check a sample of reconciled deals against expected ARR.
6. Make the custom ARR property read-only.
7. Rename it with an "OLD -" prefix (e.g. "OLD - Annual Recurring Revenue (ARR)") so it's clearly marked retired.
8. Update any reports/dashboards/workflows referencing the custom property to reference `hs_arr` instead.
9. Confirm and document: `hs_arr` is live and accurate, custom property fully archived (read-only, prefixed, no active references).
