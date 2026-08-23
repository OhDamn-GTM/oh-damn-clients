# TF-Series Session Context

Compiled handoff context across two working sessions on the TF-series tickets (TF05, TF06, TF07, TF10, TF17) — contact owner reassignment and the CPD Session custom object build. Kept for continuity when picking this work back up.

Source docs: `TBA-Firefly-Full-Session-Context.md` (session 1 — TF07 reassignment, TF17 CPD build, and the start of the postcode audit) and `TF-Series-Session-Context.docx` (session 2 — continuation of the postcode audit only, and the more current status for that workstream). Where the two disagree on Part 3 numbers, session 2 is newer and supersedes session 1.

---

## Part 1: TF07 Contact Owner Reassignment

### Bucket 1 execution
- Executed the 1,333-contact bucket 1 mapping from `TBA-Firefly-Owner-Reassignment-List.xlsx` (12 rows across 4 archived owners → 4 active regional reps).
- **One change from the original sheet**: the 731 contacts in Robert McDowell's territory went to **David Murray** (interim, short-term), per David's live sign-off on a call.
- Workbook updated and delivered as `TBA-Firefly-Owner-Reassignment-List-EXECUTED.xlsx`: Tab 1 sign-offs marked complete, Tab 3 mapping updated with the David Murray row, Tab 6 open items updated, subtotal formula-verified at 2,064.
- Execution method: HubSpot Contacts → Advanced filters → `Contact owner` + `Postal Code` (`contains exactly` on outward code lists, not `is any of`, which needs exact whole-field matches and false-negatives against full postcodes like `B15 2TT`).
- HubSpot's paste-to-filter modal ("Edit values") caps at 250 values — postcode lists were batched into ~150-220 per filter.

### McDowell → David Murray (separate, later confirmed)
- Slack thread (Gaurav Arora → Rui Calvario) confirmed **383 contact-owner-filtered + 14 postcode-filtered = 397** contacts moved from Robert McDowell to David Murray. James Cook acknowledged.
- **Note**: 397 is a different, later reconciliation pass than the original 731 estimate from the TF07 workbook. Both exist in history; 397 is the one confirmed executed via Slack.
- A HubSpot workflow ("Postal Code to Region Mapping for Rep Assignment") was built to encode this: branch on Postal Code list → set Region = North, set Contact owner = David Murray. At last review, only the David/North branch was built — if it's meant to be the full 5-region routing workflow (TF10), the other 4 regions may still be missing. Worth checking.

### Data quality finding: Wales/Cornwall mistagging in Midlands
- Audited `TBA_Territory_List_for_Assignment_-_Postcodes_to_Region_mapping.csv` (1,777 rows).
- **183 of 422 rows tagged `Region = Midlands` (43.4%) actually have County = Gwynedd, Dyfed, Cornwall, Powys, Clwyd, or Gwent** — Wales and Cornwall, not the Midlands.
- Delivered as a color-coded flagged workbook (`TBA-Territory-List-Region-Mismatch-Flagged.xlsx`) for client review.
- Client returned the file apparently unchanged (183 mismatches still present) — user instructed: treat it as final anyway (see `postal_code_mapping.xlsx`, which resolves this further in session 2, below).
- Same class of error (wrong-nation county under a rep's territory) has since turned up in every other region checked: Adrian Bell (26 Glamorgan/Wales rows), Andy Greenwood (15 Scotland rows). Likely present in Ireland (Andy Corry) and North (David Murray) too.

---

## Part 2: CPD Session Custom Object — Full Build (TF17)

Built against `TBA_Firefly_CPD_Custom_Object_Draft.docx` (later revised once by the client to fix two internal contradictions — see below).

### Object setup
- Singular: `CPD Session` / Plural: `CPD Sessions`.
- Primary display property: **Company Name** — Contact Name/Company Name aren't unique per record (one company can have multiple sessions), but Company Name is always known at creation.
- Secondary display properties: **Region** and **Preferred Date** — both reused existing Section 1 properties.

### Associations
- Contact (many-to-many), Company (many-to-many), Deal (many-to-many) — confirmed via the Data Model Builder.
- **Association label added**: "Enquiry Contact" (CPD Session→Contact limited to 1, Contact→CPD Session unlimited) — needed for email workflows to know which contact to email. "Attendee" label discussed but deliberately not created (deferred until QR matching automation is built).

### Properties (34 custom, across 4 groups matching the draft's 4 sections)
- **Enquiry & Registration (13)**: Company Name, Region, Preferred Date (display props) + Source, Contact Name, Job Title, Email Address, Telephone Number, Customer Type, Location, CPD Topic Requested, Number of Attendees, Delivery Format.
- **Scheduling & Logistics (10)**: Assigned Rep, Presenter, Confirmed Date, Confirmed Start Time, Confirmed Location or Meeting Link, Parking Available, AV Equipment Available, Lunch Required, Number of Lunch Attendees, Additional Notes.
- **Attendee Registration (4)**: Actual Attendee Count, Attendees Confirmed, Certificate Issued, Certificate Issue Date.
- **Post-CPD Follow-Up (7)**: Feedback Received, Feedback Notes, Follow-Up Completed, Opportunity Generated, Post-CPD Notes, Next CPD Topic Interest, Re-engagement Date.
- **Caught and fixed**: `CPD Topic Requested`'s dropdown option read "Fire Compartmentation Solution" (missing the "s") while `Next CPD Topic Interest` correctly read "...Solutions" — fixed to match, since the two fields need identical wording to be comparable in reporting.
- Verified via full CSV export: 34 custom + ~16 HubSpot system defaults = 50 total properties, all correctly grouped.

### Pipeline (7 stages)
Enquiry Received → Qualification Complete → Date Proposed → Date Confirmed → CPD Scheduled → CPD Delivered → Follow-Up Complete.

**Contradiction #1 (resolved)**: draft's Open Questions referenced "the same 9 pipeline stages" while Section 2 only defined 7. James Cook confirmed it was a typo — 7 is correct.

Exit gates per stage:
- **Enquiry Received**: none (by design).
- **Qualification Complete**: Customer Type, Region, Number of Attendees, Delivery Format, CPD Topic Requested required.
- **Date Proposed**: Preferred Date, Assigned Rep, Presenter required.
- **Date Confirmed**: Confirmed Date, Confirmed Start Time, Confirmed Location or Meeting Link, Parking Available, AV Equipment Available, Lunch Required, Number of Lunch Attendees required.
- **CPD Scheduled**: no field-based rule — gated by the reminder-email automation instead.
- **CPD Delivered**: Actual Attendee Count, Attendees Confirmed, Feedback Received required.
- **Follow-Up Complete**: Follow-Up Completed, Post-CPD Notes, Next CPD Topic Interest, Re-engagement Date required.

Note: initial pipeline creation left HubSpot's default "Open Stage"/"Closed Stage" placeholders in place, plus a stray "Closed" status on Qualification Complete — both caught and fixed; all 7 stages correctly "Open" now.

### Automation — Phase 1

**Contradiction #2 (resolved)**: exit gate table said the confirmation email fires at Stage 5 (CPD Scheduled); the Phase 1 Automation section said "on stage move to Date Confirmed" (Stage 4). Client disambiguated: **confirmation email = Stage 4 (Date Confirmed)**, **reminder sequence = Stage 5 (CPD Scheduled)**.

1. **Assigned Rep auto-assignment** — trigger: `Region is known` (corrected from "on record creation" as literally worded, since Region isn't captured until Stage 2's exit gate). Branch on Region → Set Assigned Rep: Scotland and Borders→Adrian Bell, Midlands→Navraj Pahl, South England→Andrew Greenwood, Ireland→Andy Corry, North England→**David Murray** (per TF07 interim decision, not the original sheet's Robert McDowell). Live/ON.
2. **Date Confirmed → confirmation email** — trigger: stage = Date Confirmed. Sends "CPD Session - Date Confirmed Email" to the Enquiry Contact. Built, OFF pending Jason's copy/sender sign-off.
3. **CPD Scheduled → reminder sequence** — trigger: stage = CPD Scheduled. Delay (7 days before, 09:00 BST) → 7 Day Reminder → Delay (3 days before) → 3 Day Reminder → Delay (1 day before) → 1 Day Reminder. Built, OFF pending sign-off.
4. **CPD Delivered → follow-up tasks** — trigger: stage = CPD Delivered. Three "Create task" actions (Day 1/7/14), each assigned via "An existing owner of the CPD session → Assigned Rep" (not the generic Owner property). Live/ON — internal tasks, no sign-off needed.

### Emails (4 built + 1 extra, Marketing → Email, type "Automated")
Tokens: First Name (Contact), CPD Topic Requested, Confirmed Date, Confirmed Start Time, Confirmed Location or Meeting Link (CPD Session). Fallbacks: "Customer" (First Name), "To be confirmed" (rest).

- **CPD Session - Date Confirmed Email** — sender fixed from an incorrect Bound support address to `ipyatt@tba-pt.com` (flagged as needing confirmation this is intended). Removed leftover duplicate sign-off text from the reused template.
- **7/3/1 Day Reminder** — same structure, differing only in "coming up in X days" framing.
- **CPD Session - Enquiry Received Email** — built at the user's request but **not in the doc's automation scope**. No Stage 1 trigger workflow built for it yet. Flagged as new scope needing Jason + James/Rui awareness.

All 4 in-scope emails are published (required for the "Automated email" dropdown to show them) but workflows remain OFF pending Jason's sign-off.

### QR attendee registration
- Technical feasibility self-confirmed for matching a QR form submission to the correct CPD Session via CPD Topic + date, using HubSpot's native "Create associations" workflow action (confirmed available for custom objects without Operations Hub; Date-property and enumeration-property matching flagged as uncertain, worth testing directly).
- Build steps discussed: QR form (First Name, Last Name, Job Title, Email, Company Name, CPD Topic Attended — needs a new Contact-level property), Contact-enrolled workflow with "Create associations" matching CPD Topic Attended + today's date, then incrementing Actual Attendee Count and setting Attendees Confirmed.
- **Reported complete by the user**, but not visually verified the way every other automation was screenshot-verified.

### Scope check finding
- The doc's "Entry Points" table describes a **public website form** (`tbafirefly.com/cpd/`) as the primary automated intake, and an **internal HubSpot form** for RIBA/MBS/Self-Generated sources (Stephen fills manually). **Neither is mentioned in the build checklist** — unclear if in scope, already exists, or is a separate future task. Not resolved.

### Still-open items (build not complete until answered)
1. DCE Online seminars — same 7-stage pipeline or separate treatment? (David/Jason)
2. Certificate issuance — fully automated on QR submission, or manual via Jason/Stephen? (Jason/David)

### Slack status
- Channel: **#boundxohdamn-tbafirefly** (Slack Connect — bot can only draft, not post directly). A full status table was drafted as a **draft reply** in thread `1784114317.183939` for manual review/send.

---

## Part 3: Postcode-to-Owner Reassignment Audit

Auditing which contacts *should* belong to each regional rep (by postcode) versus who *currently* owns them, using the client-confirmed-final territory list. Two sessions of work — session 2's status table is the current source of truth; session 1's methodology and early numbers are kept for context.

### Background (session 2)
Tracks linked tickets TF05, TF06, TF07, TF10. Goal: move contacts sitting with archived/departed reps, and contacts with no owner, onto the correct active rep per postcode-to-rep mapping.

Session 2 began from `TFReassignmentSUPPORTINGFILES.zip` (two spreadsheets + 13 text files). No single handoff doc existed — the closest equivalent was the Overview and Open Items tabs in `TBA-Firefly-Owner-Reassignment-List-EXECUTED.xlsx` (TF05 working file): sign-off list of 8 archived owners and contact counts, regional breakdown by postcode, proposed new-owner mapping, and an Open Items and Data Gaps tab with 13 unresolved questions.

`postal_code_mapping.xlsx` (uploaded in session 2) is the same 1,777-row territory list but with the Flag column updated: the 219 previously flagged Midlands rows (183 old mismatches + 36 old no-county rows) now carry researched county names instead of a generic label — this resolved 32 of the 36 no-county rows into plausible Midlands counties, confirming the other 183 as genuine Wales/Cornwall mismatches. **This update only affects Navraj Pahl's Midlands rows** — the Midlands batch files predate it and need regenerating.

### Methodology (established in session 1, reused/reverse-engineered in session 2)
1. Filter source data by `Account manager` column (not the raw `Region` column, which is inconsistent/overlapping across reps — e.g. "North" splits between Adrian Bell and Robert McDowell).
2. Cross-check `County` against geography to catch mistagging (same bug found in every region so far).
3. Split comma-joined postcode cells into individual codes; collapse London-style sub-district letters (e.g. W1A/W1B/W1C → W1); drop rows with no County or a region-mismatch Flag; drop two documented cross-owner collisions (TD12 shared between Andy Greenwood/Adrian Bell; W12 — UK London postcode under Andy Greenwood vs. Irish Eircode routing key under Andy Corry — both referenced in TF05 open item 7).
4. Sort as plain text (not numeric), matching existing batch file convention.
5. Batch into ~150 per HubSpot "contains exactly" filter (not "is any of" — false negatives).
6. Per batch: filter Postal Code only (no owner filter) → confirm total → export Contact Owner + Postal Code to CSV → cross-check every code matches source list, check for duplicate Record IDs, tally by current owner.

This method reproduced the existing Midlands batch exactly and Andy Greenwood/Adrian Bell almost exactly — the small remainder was manual removal of geographically obvious mismatches (Jersey/Perthshire under Andy Greenwood, Cardiff under Adrian Bell) done by hand, beyond the documented Midlands-only audit.

### Status by owner (session 2 — current)

| Owner | Region | Contacts checked | Already correct | Need to move | Notes |
| --- | --- | --- | --- | --- | --- |
| Andrew Greenwood | South | 1,498 | 1,331 | 167 | Verified — all 6 batches uploaded, exported, cross-checked |
| Andy Corry | Ireland | 153 | 35 | 118 | Verified — single batch uploaded, exported, cross-checked. Includes 1 no-owner contact (Brendan Lyons, T23 N73P) — a live example of the NULL-owner category from TF05 open item 12 |
| Navraj Pahl | Midlands | 790 | 5 | 785 | Confirmed accurate by the requester; figures predate session 2. Batch files now slightly out of date following `postal_code_mapping.xlsx` update, not yet regenerated |
| Adrian Bell | Scotland and Borders | 346 | 13 | 333 | Not independently verified in session 2 — only source postcode batches built/checked against territory sheet; no HubSpot export received |
| Robert McDowell | North | n/a | n/a | n/a | Postcode batches built and delivered (304 codes, 3 files) but not yet run through HubSpot at all — next owner to take through the upload/export/verify cycle |

Batches delivered in session 2:
- Robert McDowell: 304 postcode districts, 3 batch files. All raw counties consistent with North England, no geographic mismatches found.
- Andy Corry: 151 codes reduced to 150 (excluding the W12 collision), 1 batch file. Covers all of Ireland (NI postcodes + RoI Eircode routing keys).
- Andy Greenwood: all 6 pre-existing batch files resent on request.

### Session 1 in-progress numbers (superseded by the table above, kept for history)
- **Midlands (Navraj Pahl) — COMPLETE**: 422 total rows → 183 Wales/Cornwall mismatch, 36 no-county → 378 clean verified outcodes, batched 3×. 790 checked, 5 already correct, 785 need to move. Breakdown: Chris Worby (Deactivated) 550, Andrew Greenwood 106, Stephen Neville 76, David Murray 36, Chris Boam 7, Dave Steel (Deactivated) 7, Navraj Pahl 5, Thomas Brookes (Deactivated) 2, Andy Corry 1.
- **Scotland and Borders (Adrian Bell) — COMPLETE**: 443 total rows → 26 Glamorgan/Wales mismatch, 2 Guernsey/Isle of Man held out pending confirmation → 494 clean verified outcodes, batched 4×. 346 checked, 13 already correct, 333 need to move. Breakdown: Daniel Gordon (Deactivated) 241, Stephen Neville 37, Chris Worby (Deactivated) 37, Adrian Bell 13, David Murray 13, Andrew Greenwood 3, Chris Boam 1, Thomas Brookes (Deactivated) 1.
- **South England (Andy Greenwood) — IN PROGRESS (3 of 6 batches)**: 623 total rows → 15 Scotland mismatch, 2 Jersey/Isles of Scilly held out → 762 clean verified outcodes, batched 6× (150×5 + 12). Batches 1-3: 927 checked, 816 already correct, 111 need to move. (Session 2 completed all 6 batches — see current table above: 1,498 checked, 1,331 correct, 167 need to move.)
- **Ireland (Andy Corry)** and **North England (David Murray)** — not started as this specific postcode-verification exercise in session 1 (David Murray separate from the McDowell interim 397-contact reassignment already done in Part 1).

### Cross-region open items
1. **Stephen Neville and Chris Boam** appear as current owners of a large number of contacts across every region checked (237 combined across Greenwood, Corry, Navraj, Adrian Bell per session 2's count), but neither is on the original TF05 archived-owner sign-off list. Employment/active status not confirmed — resolve before any bulk reassignment touches their contacts. (Chris Boam identity: appears in Midlands (7), Adrian Bell (1), Andy Greenwood (5+) = 13+ contacts and counting, per session 1.)
2. **David Murray** appears in every region (Midlands 36, Adrian Bell 13, Andy Greenwood 8+). Some may be legitimate given his interim North England role — not resolved.
3. **Robert McDowell** not yet run through HubSpot verification — same process as the other four: filter by his batch postcodes, export contact owners, share the CSV.
4. **Navraj Pahl's batch files** predate the `postal_code_mapping.xlsx` update — should be regenerated to include the 32 previously-unverifiable rows that now resolve to real Midlands counties, before any further Midlands batches are uploaded.
5. **Adrian Bell** not verified against a HubSpot export — the 333-of-346 figure is only internally consistent, not independently confirmed.
6. **The NULL-owner contact category** (TF05 open item 12) was scoped from the start but never started as its own workstream. One example surfaced in Andy Corry's batch (Brendan Lyons).
7. **Cross-region active-rep strays** — Andrew Greenwood owns Midlands/Adrian Bell contacts outside his own territory; Andy Corry owns 1 Midlands contact. Unclear if deliberate or error.
8. **Held-out borderline geography** (excluded from batches, not yet decided): Guernsey/Isle of Man (Adrian Bell's territory), Jersey/Isles of Scilly (Andy Greenwood's territory).
9. Remaining open items from the original TF05 workbook (count discrepancies, missing org chart, unreconciled contact totals, and others) are unchanged and listed in full in the Open Items and Data Gaps tab of `TBA-Firefly-Owner-Reassignment-List-EXECUTED.xlsx`.

### Deliverables sent
- Session 1: Slack message (sent, not just drafted) to Rui/James — Midlands 785-of-790 breakdown, asking approval for the archived-owner segment and flagging Stephen Neville/Andrew Greenwood/Chris Boam as needing individual checks before bulk-moving. James Cook asked for this to be compiled into **one consolidated document for client approval** — not yet built at end of session 1.
- Session 2: `RobertMcDowell-CLEAN-Batch1/2/3.txt`, `AndyCorry-CLEAN-Batch1.txt`, `AndyGreenwood-CLEAN-Batch1.txt` through `Batch6.txt` (resent), `TF-Series-Reassignment-Summary.docx` (tabular summary of all four verified/partially-verified owners: Greenwood, Corry, Navraj, Adrian Bell).

---

## Next steps (pick up here)

1. Run Robert McDowell's batches (304 codes, 3 files ready) through the same upload/export/verify cycle as the other four owners.
2. Get a HubSpot export for Adrian Bell to independently verify the 333-of-346 figure.
3. Regenerate Navraj Pahl's Midlands batch files to reflect the `postal_code_mapping.xlsx` update (32 rows now resolve to real Midlands counties).
4. Build clean outcode lists for Ireland/North England if not already covered by the McDowell/Corry batches above.
5. Resolve Chris Boam's identity and get a decision on Stephen Neville's and David Murray's cross-region contacts (reassign or leave, per person/region).
6. Get a decision on the 4 held-out borderline geography cases (Guernsey/IoM/Jersey/Scilly).
7. Start the NULL-owner contact workstream (TF05 open item 12) — Brendan Lyons is a live example.
8. Compile the consolidated client-approval document James requested, covering all 5 regions, clearly separating "already executed" (TF07 bucket 1, McDowell→David 397) from "pending approval" (this postcode audit work).
9. Separately: get Jason's sign-off on the 4 CPD emails, resolve the DCE/Certificate open questions, decide on the Enquiry Received email's scope, and check whether the website/internal intake forms are actually in scope for TF17.
