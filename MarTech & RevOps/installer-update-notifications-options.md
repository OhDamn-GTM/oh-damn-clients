# Preferred Installer Update Notifications: Approach Options

## Overview

Jason wants an automated, GDPR-compliant way to notify preferred installers whenever drawings or product pages are updated. Critically, this runs on a fresh opt-in form rather than existing website contact data — installers need to actively consent to this specific notification. Three ways to build this natively in HubSpot.

## What all three options share (non-negotiable for GDPR)

- A dedicated communication subscription type (e.g. "Installer Drawing & Product Updates") separate from general marketing — opting into this doesn't imply opting into anything else.
- An unticked, explicit consent checkbox on the form itself. No pre-checked boxes, clear language on what they're signing up for and how often.
- A one-click unsubscribe on every notification, honoured immediately and specific to this subscription type only.
- The form creates or updates a contact but does not merge in or infer consent from any existing marketing subscription status that contact may already have.

## Option A: Native form and manually-triggered send (fastest to launch)

HubSpot native form on the installer-facing page, tied to the dedicated subscription type. An active list segments everyone opted in. When a drawing/product page updates, marketing sends a HubSpot marketing email to that list manually — no workflow trigger.

## Option B: Native form and property-triggered workflow (automated, no new tooling)

Same opt-in form and subscription type as Option A. Add a property on the relevant record (e.g. "Content last updated" date on a Product custom object, or on the CMS page if tracked as a property) that whoever publishes the update ticks/updates as part of their existing publish routine. A workflow triggers automatically off that property change and sends the notification. Fully automated from that point on.

## Option C: Native form and scheduled content check (fully automated, no manual step — requires a new purchase)

Same opt-in form and subscription type. HubSpot CMS has no native "page published" webhook, so this checks for updates instead of reacting to a live event: a scheduled automation runs at a regular interval (e.g. hourly), checks CMS pages via HubSpot's API for anything updated since the last check, then triggers the notification.

Building the scheduled check requires **Operations Hub (Professional or Enterprise)** for the programmable automation piece — not currently on the account, so this option requires a new purchase. Optionally scoped to per-product relevance (installer only notified about drawings/products they actually work with) rather than a blanket "anything changed" blast.

## What we need from Jason and David

- A steer on how strictly "automated" needs to be interpreted for launch — Option A ships fastest but leans on a person, Option B is a no-new-spend middle ground, Option C removes the person entirely but adds licensing cost.
- Whether Operations Hub's cost is worth taking on for this use case alone, or only if there are other planned use cases.
- Whether notifications should be blanket (any update, any installer) or targeted by product/drawing relevance.
- Sign-off on the consent language and subscription-type naming before the form goes live — this is the GDPR-sensitive part.
