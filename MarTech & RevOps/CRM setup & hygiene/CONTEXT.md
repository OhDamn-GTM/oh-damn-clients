# CRM setup & hygiene

CRM structure, data quality, and related processes.

Key open items (see [hubspot-config.md](hubspot-config.md)):
- Contacts: RED — 98.9% (12,335 of 12,478) have no lead status; 14.3% no owner; 14.8% no company association; 34 archived owner IDs still hold assigned contacts.
- Pipeline & Deals: RED — 7 pipelines incl. duplicates, 87% stale, 69% no value, 0 closed won ever.
- Users & Access: RED — 14 super admins (target 2-3: Robert McDowell, David Murray, one Bound admin); 34 archived owner IDs still active.
- Properties: AMBER — 107 custom contact properties across 5 groups; Eventbrite group (17) likely orphaned; only 5 custom deal / 6 custom company properties (deal record underbuilt).
- Raw object exports for reference: [data/](data/) (Companies, Contacts, Deals, Meetings, Projects, Tickets, Workflows, Course Attendance CSVs).
