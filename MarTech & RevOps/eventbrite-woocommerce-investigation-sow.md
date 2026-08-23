# Scope of Work: Eventbrite WooCommerce Investigation

Type: Investigation, not delivery. Sprint week: Fri 7th – Thu 13th Aug 2026. Due: 13 Aug 2026 (end of sprint week).

## Priority

Background/secondary work, progressed opportunistically alongside the sprint's main deliverables. Not a blocker for anything else.

## Objective

Assess the feasibility and effort of replacing Eventbrite with WooCommerce for the installer training booking and checkout flow, versus holding this and building it natively in HubSpot as part of a possible future full website migration.

## Background

Jason (Head of Marketing) has approved moving off Eventbrite; WooCommerce is his recommended interim option, though his ultimate goal is to have this directly in HubSpot. Jason is separately briefing TBA's web developers (Capture) on the same process, but their lead contact is on holiday until the following week — this assessment is based on the process maps alone rather than waiting on them.

## Scope in

- Steps 1–7: venue selection → date/trainee count selection → checkout (contact and per-trainee details, pricing) → order placement. This is the process currently hosted in Eventbrite and embedded on the Firefly website.
- Step 8, booking confirmation email — in scope as the direct output of checkout (auto-confirmation, pre-event reminder via HubSpot).

## Scope out

Everything from "installer training delivered" onward is explicitly excluded — a separate, largely manual downstream process, possibly worth a future ticket but not part of this investigation:

- QR code check-in
- ID card/certificate generation (currently manual: Canva editing, formula-calculated spreadsheet, physical Card Exchange printer)
- The shared T-drive process
- The monthly installer database merge sent to Capture

## Deliverable

A short recommendation only (not a build) covering:
- Effort/timeframe to implement the WooCommerce route now
- Effort saved or duplicated if a HubSpot migration happens later instead

## References

- **Process map 1**: Eventbrite/checkout flow (Firefly website → Eventbrite → Checkout → Booking confirmation). Jason: "I've mapped out the process for installer training and booking on the online system. I've also reached out to our web developers with the same — and an initial brief so we can get something in the calendar. Our lead contact is on holiday until next week... it's not our No1 priority as getting the firefly technical/sales team fully onboarded and using HubSpot is. However, we do seem to be making some progress outside of that."
- **Process map 2**: Broader booking-to-database flow (Installer training booked → delivered → Firefly shared folder → Packs posted → Installers added to database). Jason: "this is a flowchart I've already shared for the broader process. The chart I sent earlier is more specific to moving from Eventbrite to integrating directly into the FF website."
