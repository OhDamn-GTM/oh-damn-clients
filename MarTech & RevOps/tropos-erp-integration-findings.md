# Tropos ERP Integration — Findings Report

14 August 2026

## Context

David raised this on the 31 July standup: a significant share of Firefly's sales (stockist orders, word-of-mouth, over-the-counter) transact through their ERP, Tropos, and never touch HubSpot — that side of the business is invisible in reporting. Ask: investigate whether HubSpot could pull data from Tropos to make it visible. **Flagged by the client as early-stage and exploratory, not an urgent build.**

## What we found

**What Tropos is** — an Epicor ERP product built for process manufacturers (food, beverage, pharma, metals, chemicals), a reasonable fit for Firefly's manufacturing operation. Handles production planning, materials tracking, compliance.

**No native connector exists** — no pre-built integration between Tropos and HubSpot in either platform's marketplace/ecosystem. Not unusual for niche ERPs, but any connection has to be built rather than switched on.

**No public API documentation found (key finding)** — Epicor's newer product, Kinetic, has extensive public REST API documentation; Tropos does not. One independent review source lists "no open API support" as a specific limitation. Third-party integration vendors describe connecting to Tropos via older, database-level methods (ODBC, OLEDB, web services) rather than a modern REST API.

**Practical implication** — if Tropos does have some form of API/data access, it's likely more limited or harder to work with than a standard modern integration. Realistic routes: a middleware/connector tool built for legacy ERPs (e.g. Codeless Platforms, Jitterbit), or custom development against whatever access Tropos exposes. Either way, more build effort than a typical "plug two systems together" integration, and would sit outside HubSpot given Firefly doesn't have Operations Hub.

**Hosting** — Epicor offers Tropos as cloud-hosted, so it's plausible Firefly's instance is cloud-based, but this can't be confirmed externally.

## Questions we need from the client

- Which version of Tropos is Firefly running, and is it cloud-hosted or on-premise?
- Does their instance have any API or data-export access enabled, and if not, would that need enabling/licensing through Epicor?
- Who manages Tropos day-to-day? Likely finance, operations, or an external IT provider — not Jason directly, given his role. Worth confirming the right technical contact.

## Recommendation

Treat this as genuinely early-stage. Integration is technically possible in principle, but practical cost and approach depend entirely on details only the client can provide. Right framing for now: confirm interest in principle, get the three questions above answered, and scope properly once we know what Tropos actually exposes.
