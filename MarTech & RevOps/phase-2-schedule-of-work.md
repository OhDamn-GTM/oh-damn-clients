# Phase 2 — Schedule of Work

## Context

Client contact: Ali, CCO at Halo Solutions. Joined ~4 weeks before this SOW. Hard deadline: end of August 2026 to have the three critical priorities working reliably. Verbally approved the SOW; contract in progress.

Key people on the Halo side:
- **Ali** — CCO, driving the project, primary point of contact for scope and decisions.
- **Charlie** — Head of Partnerships, primary day-to-day HubSpot user. Hasn't worked with a full CRM at scale before — needs onboarding into the process. Workshop with Ali and Charlie planned for **19 August**.

Notes from the Tuesday call:
- The Sales Lead object is not activated — deals go straight to pipeline, skewing closed-lost data. Must investigate before any pipeline changes.
- The Partner HubSpot setup was inherited by Charlie and wasn't designed for the current use case. Workflows and automated emails need review before touching the pipeline.
- The Xero connector issue is expected to unblock most day-to-day reporting once fixed.

## Hour ceiling

| | |
| --- | --- |
| Total hours purchased | 40 (30 paid + 10 goodwill) |
| Maximum hours we can spend | **40 — not one minute over without James approving additional scope** |
| Estimated hours so far | TBC |
| Hours remaining | TBC |

## Deliverables

### Phase A: Foundations

| Ref | Deliverable | Owner | Notes | Hours |
| --- | --- | --- | --- | --- |
| A1 | ARR consolidation | OhDamn | hs_arr vs custom ARR property state, mismatches, multi-currency plan, historic data migration before archiving custom property | 2 |
| A2 | Price book clean up | OhDamn | Product count, unused/duplicated items, billing frequency corrections, prioritize most-used products | 3 |
| A3 | Multi-currency FX setup | OhDamn | Confirm FX never previously enabled; check settings/integrations impact; expected effect on existing deal values | 2 |
| A4 | Company and deal card structure | OhDamn | Deals with no company associated, duplicate company records beyond what Ali already cleaned, rollup config for Annual Total Spend / ARR | 3 |
| A5 | Deal type property implementation | TBC | Property exists (new business/upsell/renewal) — retroactive tagging manual vs automated by stage/name pattern | 2 |
| A6 | Partnerships pipeline retirement | TBC | Active deal count in Partnerships pipeline, disposition, Charlie consultation — **flag for 19 Aug workshop** | TBC |
| A7 | Sales Lead object investigation | TBC | **IMPORTANT**: object not activated, deals skew closed-lost data. Need current closed-lost picture, activation risk assessment, recommendation before any pipeline changes | TBC |
| A8 | Renewal and expiry property rationalisation | TBC | 6 properties doing the same job — recommend keeping 3 (Current Contract Start Date, Halo Licence Expiry, Payment Renewal Date); migration + completeness check | TBC |
| A9 | Renewal workflow build | TBC | Automated workflow on Halo Licence Expiry: alert deal owner at 90/30/0 days; check for conflicting workflows, confirm notification recipients/method | TBC |
| A10 | Permissions audit and restructure | TBC | Super admin count, who needs admin vs standard access, recommended structure — handle carefully to avoid locking people out mid-project | TBC |
| A11 | Partner HubSpot workflow review | TBC | **PREREQUISITE before any pipeline changes.** Charlie inherited this setup — audit active workflows/automated emails on Partnerships pipeline, flag anything mission-critical or breakable. Needed before 19 Aug workshop | TBC |

### Phase B: Sales Hub

| Ref | Deliverable | Owner | Notes | Hours |
| --- | --- | --- | --- | --- |
| B1 | Xero integration upgrade | TBC | **HIGHEST PRIORITY** for unblocking reporting — current integration deprecated. Recommend replacement, data mapping, product matching, migration risk. Estimate includes discovery, setup, testing, validation | TBC |
| B2 | HubSpot quotes scoping | TBC | Contingent on Charlie's sales team buy-in. Scope migration from Xero quotes to HubSpot quotes, templates needed. Scope only — don't build until 19 Aug workshop confirms buy-in | TBC |
| B3 | Sales team playbook | TBC | One-pager: deal creation, line item selection, stage gates, deal closure. Draft after Phase A decisions confirmed; James reviews before sharing with Halo | TBC |
| B4 | Training session | TBC | Short session with sales team once Phase A is stable. Ali arranges attendance. Do not schedule until Phase A confirmed complete | TBC |
| B5 | Missive and HubSpot integration investigation | TBC | Check if Missive supports HubSpot integration now — scope if yes; otherwise configure HubSpot Sales Chrome extension for Gmail logging. Lower priority — flag if hours run short | TBC |

### Project management and communication

| Ref | Deliverable | Owner | Notes | Hours |
| --- | --- | --- | --- | --- |
| PM1 | Weekly standups with Ali | James | 20-30 min accountability calls, James leads | N/A |
| PM2 | Ali and Charlie workshop | James & Rui | 19 August, 30-60 min, James facilitates | 1 hr |
| PM3 | Weekly progress updates | James & Rui | Written update to Ali after each standup: completed, next, decisions needed. Rui drafts, James reviews and sends | N/A |

## Process

Team input deadline: **13 August EOD**. For each item provide estimate (or TBC + what's needed), questions, recommendations, and blockers.

Rui assigns owners and collates input → James reviews and confirms timeline → sent to Ali.

The 19 August workshop with Ali and Charlie resolves anything that needs client input.
