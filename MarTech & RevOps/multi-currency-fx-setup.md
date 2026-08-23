# Multi-Currency FX Setup and Update Cadence (A3)

## Objective

Confirm the current state of multi-currency in the HubSpot portal, close the gap where EUR/USD deal values were showing unconverted in reports, and document the exchange rate update cadence.

## Current state

Multi-currency is enabled and already in use. Company currency: GBP. Three additional active currencies: EUR, USD, CAD (four total).

Automatic exchange rate updates are on, frequency Monthly, next scheduled update **03/09/2026**. Rates pulled automatically by HubSpot's own feed — no manual action needed from the Halo team.

For open deals, the exchange rate updates live as HubSpot's rates refresh. For closed deals, the rate locks at close — converted value doesn't drift with market rates afterward.

## What this confirms and resolves

1. Multi-currency was already enabled — no setup action was required.
2. `Amount in company currency` was already converting correctly, but `Total contract value`, `Annual contract value`, and `Annual recurring revenue (hs_arr)` had no equivalent converted property — reports built on those three fields showed raw EUR/USD figures unconverted alongside GBP.
3. Three new calculation properties created to close the gap: `Total contract value in company currency`, `Annual contract value in company currency`, `Annual recurring revenue in company currency`. Each multiplies the native metric by the deal's own Exchange rate property.
4. Verified against live deal records.

## Reports

The "New Deals (This Year)" report has been updated to use the three new company-currency properties. Any other report built on the native (unconverted) versions of these three fields needs the same swap — replace under Manage properties, save. **This rollout is in progress across the remaining reports in the portal.**

Recommendation for future reports: always use the company-currency version of a currency-based deal metric, never the native version.

## Integrations reviewed — Xero

The Xero integration syncs invoice data into a dedicated Invoice object. The Xero Total field maps to `Amount billed` (native currency, no conversion at sync). HubSpot separately and automatically calculates `Amount billed in company currency` at 100% fill rate across all invoices — this already performs the conversion, no additional setup needed.

Related: see [CRM setup & hygiene/arr-property-consolidation.md](CRM%20setup%20%26%20hygiene/arr-property-consolidation.md) — `hs_arr` does NOT currently use company-currency conversion, and whether it should is pending Ali's decision.
