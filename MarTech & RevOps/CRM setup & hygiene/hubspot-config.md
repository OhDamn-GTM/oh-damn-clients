# TBA Firefly - HubSpot Configuration

## License / tooling available
- Sales Hub Enterprise (largely underused prior to this engagement)
- Service Hub seats allocated, 0 tickets exist as of audit
- Operations/Data Hub available and unused - this is the path for the calculator API integration James referenced on the call. Custom objects, programmable automation, and data sync are all on the table for scoping, not blocked by license tier.

## Audit health scorecard (baseline, Sprint 1)
| Area | Status | Key finding |
|---|---|---|
| Contacts | RED | 98.9% (12,335 of 12,478) have no lead status |
| Companies | AMBER | 19.3% (1,082) have no associated contacts |
| Pipeline & Deals | RED | 7 pipelines incl. duplicates; 87% stale; 69% no value; 0 closed won ever |
| Properties | AMBER | 107 custom contact props; Eventbrite group (17) likely orphaned |
| Workflows | AMBER | 27 active workflows, logic not yet individually reviewed |
| Forms | GREEN | 18 native forms, no issues |
| Lists | AMBER | 100+ lists, composition/freshness unverified |
| Users & Access | RED | 14 super admins (target 2-3); 34 archived owner IDs still active |

## Pipelines (7 found, consolidation in progress)
- **TBA Protective Technologies Ltd Sales Pipeline** - 7 stages, currently generic HubSpot defaults, not yet customized to Firefly's sales language
- **CPD Presentations** - 3 stages, legitimate separate swim lane, keep
- **Testing Pipeline** - 5 stages, likely product/materials testing, not sales; confirm with Robert whether it stays in deals or moves out
- **TBA Training Pipeline** - stages tbc
- **Exhibitions Follow ups / Exhibition follow up / Chris W's Exhibition follow ups** - 3 near-duplicate pipelines, governance failure. **TF04: built and currently in sales-team trial.**

## Contact status
- 12,478 total contacts; 12,335 (98.9%) no lead status
- 1,785 (14.3%) no owner
- 1,848 (14.8%) no company association
- 550 opted out of all email
- 34 archived (ex-employee) owner IDs still hold assigned contacts - those contacts are effectively dead-ended

## Territory / owner mapping
- Region-to-owner mapping done by UK postcode, ~1,780 postcode rows, 5,502 contacts reassigned in the associated bulk file
- Owners: Andy Greenwood (South, 623 postcodes), Adrian Bell (Scotland & Borders, 443), Navraj Pahl (Midlands, 422), Robert McDowell (213), Andy Corry (Ireland, 76)
- **Territory mapping V1.1 is signed off, including the Scotland & Borders rename.** This is settled, not open.
- **TF10 (regional routing workflow): built, not yet live.** Territory sign-off was the blocker, that's now cleared, so this is ready to activate, not still in scoping.

## Properties
- 107 custom contact properties across 5 groups: contact info (66), Eventbrite (17, likely orphaned), firefly_installation_quiz (13), firefly_installation_course_feedback (10), sales_properties (1)
- Only 5 custom deal properties and 6 custom company properties - deal record underbuilt relative to contact record
- Bound Revenue Roadmap (Company object) and Bound Sprint (Ticket object) property groups to be created as part of Foundations gate

## Users & access
- 45 total users, 14 super admins (target: Robert McDowell, David Murray, one Bound admin)
- 0 sequences currently exist
- 0 tickets exist in Service Hub despite seats being allocated (Gaurav's Phase 3 build item)

## Customer journey mapping
- Miro board holds customer-journey maps v1 and v2, referenced directly in the tickets (not a separate standalone asset)

## Known issues / platform limitations
- Eventbrite integration status unconfirmed, may be inactive and just generating clutter
- Stockist/distributor companies (no head office) don't fit the standard key-account-owns-the-project model - flagged by Robert as an edge case for the Projects/multi-site work
