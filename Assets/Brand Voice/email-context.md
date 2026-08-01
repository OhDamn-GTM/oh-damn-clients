# Min-It — Cold Email Project Context

_Working notes and deliverables from the chat session on 2026-07-28._

---

## 1. What Min-It Is (from Brand_QA questionnaire)

**Category.** A loan management / lending software platform. Primary category: "loan management system / software." Secondary: loan origination system, lending platform, consumer lending software, payments processing. Min-It is the software non-bank lenders run their loan book on, not a lender itself.

**What it is NOT.** Not a lender or finance provider, neobank, BNPL platform, debt-collection agency, generic CRM, accounting platform, payment-processor-only, broker aggregator, credit bureau, or e-signing tool. It does not lend or hold funds.

**Brand.** Australian-owned, Brisbane-based (Eagle St HQ) with a distributed dev team. Founded 2006. Bootstrapped / owner-funded. 11–25 staff. 50–150 customers. Core identity is a deliberate paradox: **trusted heritage (since 2006) + modern rebuild (cloud-native challenger).** Archetype: Sage + Caregiver. Differentiators vs incumbents (finPOWER, BizCore): flexibility, hands-on founder-led support, fast go-live, AU-native compliance and payments depth.

**Offer.** End-to-end lending infrastructure — origination, servicing, compliance, payments — "without the enterprise price tag or the build-it-yourself burden." Signature promise: **"compliance built in, not bolted on."** SaaS multi-tenant on Azure AU. Live in ~7–10 working days. Priced as flat platform fee + usage fees.

**Products / features.**

- **Min-It LMS** — loan management, servicing engine for the full lifecycle.
- **Min-It CRM** — origination, client management, compliance tooling.
- **Member Portal** — borrower self-service.
- **Payment Portal** — instalments, disbursements, reconciliation, payout tracking.
- Digital contract generation & e-signing.
- Multi-channel comms, real-time notifications.
- Automated workflows: decisioning rules, contract generation, payment scheduling, dishonour handling, notifications.
- Open API and webhooks (B2C and broker/aggregator portals).

**Compliance posture.** SOC 2 and ISO 27001 in progress (not yet certified). ASIC / NCCP / National Credit Code, Privacy Act 1988 / APPs, AML/CTF (AUSTRAC) KYC/PEP/sanctions. Australian data residency on Azure AU.

**US context (secondary market).** US integrations in development (payments: GoCardless / Usio / PayNearMe; bank verification: ValidiFI; credit: Accelitas / Zest AI / Equifax US; income: Argyle; ID/KYC: Socure / Mitek). US clients: Sunshine Loans, Enable Loans. Exhibiting at LEND360 (Austin, October).

---

## 2. Voice for Email Outreach

**Emotional target (cold email):** "This is relevant to a real problem I have, and it's not generic spam — they actually get my world." Goal: a reply or short intro call. **One clear CTA only.**

**Voice settings applied to email:**

- Compliance-led and relevant, not salesy. Anchored to a real pain.
- Formal-leaning but human (Formal 2, Corporate→Human 4). Founder "I/we," address reader as "you / your team."
- Confident, plain-English, concrete (Confident 4, Plain English 2, Concrete 2). Proof points as specifics.
- Serious register, dry humour at most, no emoji on outbound.
- Signature phrases: "compliance built in, not bolted on," "audit-ready," "configurable," "since 2006," "Australian-hosted," "live in days."
- Banned words: frictionless, seamless, next-generation, AI-powered, best-in-class, world-class, cutting-edge, robust, leverage, synergy, revolutionary, game-changing, unlock.

**Nuance:** LinkedIn DMs earn the meeting through dialogue (open a conversation), whereas cold email carries a single clear CTA.

**US "efficiency-led" track (used in this sequence):** speed and automation, ROI, modern challenger, punchy and direct, time-to-funding, stack consolidation / fewer tools. Reserved for /us outreach; lead with speed-to-funding and consolidation.

---

## 3. Sequence Brief

- **Target:** US medium lender (self- or investor-funded). Titles: VP Lending, VP Operations, Chief Lending Officer, Head of Originations, Director of Lending Operations. Pains: outgrown current system, funder/investor wants better reporting and controls, need to scale, manual/reconciliation errors, integration. This is Min-It's centre of gravity.
- **Approach:** strengths-first, not displacement (hard to prove displacement value over email). Specific, not generic. Feature-anchored to build trust.
- **Structure:** Email 1 educational, Email 2 problem-focused, Email 3 case-study-based, Email 4 FOMO-driven.
- **Rules:** 3 versions per step (F / Z / V-shaped reading patterns) with personalised subject lines. Each body under 700 characters. No em-dashes, no numerals, no special characters beyond merge fields. Low-barrier CTA ("reply with a yes").
- **Honesty guardrails:** SOC 2 / ISO 27001 and named US integrations left out of copy since they are in progress / in development.

Version key: **A = F-shaped** (front-loaded, scannable), **B = Z-shaped** (minimal, high whitespace), **C = V-shaped** (broad open, funnel to one CTA). Tokens: `[First Name]`, `[Company]`.

---

## 4. Final Copy (feature-anchored version)

### EMAIL 1 — Educational

**Subject 1A:** [Company]'s lending stack, one question
**Body 1A:**
Hi [First Name],
Most growing lenders run origination, servicing, payments and compliance across separate tools. Every handoff is where data gets rekeyed and reconciliation breaks.
Min-It puts the full lifecycle in one place. The CRM handles origination and compliance, the LMS runs servicing, and the Payment Portal covers disbursements, reconciliation and payout tracking. Dishonour handling and notifications run automatically.
I put together a short breakdown of how that fits a lender your size.
Want me to send it? Reply with a yes.
Sid

**Subject 1B:** a cleaner way to run [Company]
**Body 1B:**
Hi [First Name],
One platform for origination, servicing, payments and compliance beats four tools stitched together.
Min-It gives you a servicing LMS, an origination CRM, a borrower Member Portal, and a Payment Portal that reconciles as it goes. Compliance sits inside the workflow, not bolted on after.
Curious how it maps to your setup? Reply with a yes and I will walk you through it.
Sid

**Subject 1C:** scaling [Company] without the stack sprawl
**Body 1C:**
Hi [First Name],
Every lender wants to grow the book. Few plan for what growth does to their tooling.
Min-It was built for exactly that. Configurable workflows, automated decisioning and payment scheduling, digital contracts with e-signing, and an open API so it fits the stack you already run. Close to two decades of real lending operations sit behind it.
Worth a short overview? Reply with a yes.
Sid

### EMAIL 2 — Problem-focused

**Subject 2A:** the reconciliation problem at [Company]
**Body 2A:**
Hi [First Name],
A quick one. When a lender outgrows its first system, the pain shows up in servicing, not origination.
Repayments land in one tool, the loan book lives in another, and someone reconciles the two by hand. Errors creep in. Reporting slips.
Min-It closes that gap. The Payment Portal handles instalments, disbursements and reconciliation in the same place your loan book lives, with dishonour handling automated.
Is manual reconciliation eating time at [Company]? Reply with a yes and I will show you how we fix it.
Sid

**Subject 2B:** [First Name], where does the week go
**Body 2B:**
Hi [First Name],
Manual servicing quietly steals the most expensive hours in a growing lender.
Payment files by hand. Reconciliation by hand. Reports pulled from three places.
Min-It automates the servicing engine, reconciles payments as they land, and pushes real-time notifications, so your team runs the book instead of chasing it.
Sound familiar? Reply with a yes.
Sid

**Subject 2C:** what growth is costing [Company] behind the scenes
**Body 2C:**
Hi [First Name],
Growth looks great on the origination side. Behind the scenes it can get ugly.
More loans mean more manual reconciliation, more payment handling, more compliance checks across tools that were never meant to talk.
Min-It absorbs that load. Automated payment scheduling, dishonour handling, and a Payment Portal that tracks every payout, all under compliance built into the workflow.
Want to see where the time leaks are? Reply with a yes.
Sid

### EMAIL 3 — Case study

**Subject 3A:** how Sunshine Loans handles this
**Body 3A:**
Hi [First Name],
Thought a real example might land better than a pitch.
Sunshine Loans needed to grow the book without adding headcount for every process. They moved origination, servicing and payments onto Min-It. The Member Portal took borrower self-service off their desk, the Payment Portal handled reconciliation, and automated workflows carried the compliance load.
Less manual servicing, cleaner reporting, a platform that flexes as products change.
Want the short version? Reply with a yes and it is yours.
Sid

**Subject 3B:** [First Name], a lender a lot like [Company]
**Body 3B:**
Hi [First Name],
Enable Loans had the same goal you likely do. Scale the book, keep control, keep the funder happy.
They run origination, servicing and payments on Min-It, with digital contracts and e-signing speeding funding, and reconciliation handled inside the Payment Portal.
The same playbook could fit [Company].
Want the story? Reply with a yes.
Sid

**Subject 3C:** from spreadsheets to a real platform
**Body 3C:**
Hi [First Name],
Plenty of lenders start on spreadsheets and outgrown systems. The ones who scale well switch before the cracks widen.
Sunshine Loans did exactly that. Consolidating onto Min-It, they cut manual servicing with automated workflows, tightened compliance inside the CRM, and gave their funder reporting they could stand behind.
A fair picture of the next stage for [Company].
Want the case study? Reply with a yes.
Sid

### EMAIL 4 — FOMO

**Subject 4A:** [Company] and our US onboarding cohort
**Body 4A:**
Hi [First Name],
Last note from me for now.
We stay hands on with every onboarding, so we take on only a small number of new US lenders at a time, and our next cohort is filling.
With Min-It live, you get the servicing LMS, origination CRM, Member Portal and reconciling Payment Portal from day one, wired to your stack through our open API.
We are also in Austin this fall for the big lending conference.
Want to hold a spot, or meet in Austin? Reply with a yes.
Sid

**Subject 4B:** closing the loop, [First Name]
**Body 4B:**
Hi [First Name],
Quick and final.
Our onboarding is hands on, so US places are limited and the next ones are going.
Min-It gives you origination, servicing, payments and a borrower portal in one place, with compliance built in and go-live in days rather than quarters.
If timing matters for [Company], now is the moment.
Reply with a yes and I will hold your place.
Sid

**Subject 4C:** the window for [Company]
**Body 4C:**
Hi [First Name],
I have shared the idea, the problem it solves, and proof it works. So here is the honest close.
Because we build alongside each lender rather than run a ticket queue, we onboard only a handful of new US clients at once. You would get the full platform, LMS, CRM, Member Portal, Payment Portal and open API, with close to two decades of lending operations behind it.
That window is open now. Reply with a yes.
Sid

---

## 5. Open Items / Next Steps

- Optional: a version naming a couple of in-development US integrations, once confirmed safe to reference.
- Optional: US-vs-AU variants of the four emails.
- Optional: add a hard metric to Email 3 from Sunshine Loans or Enable Loans (would reintroduce a numeral against the no-digits rule).
- Confirm official product name spelling everywhere: **Min-It** (hyphen, per legal / rate card), module names **Min-It LMS** and **Min-It CRM**.
