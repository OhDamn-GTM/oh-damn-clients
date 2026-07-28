# Min-IT Website Copy — Session Context

> Handoff doc for the Min-IT website copywriting work. Captures the brief, source
> material, decisions made, open questions, and all copy produced so a future
> session (or teammate) can pick up without re-deriving context.

_Last updated: 2026-07-28_

---

## 1. The brief

Write website copy for **Min-IT** — a lending software platform for Australian
non-bank / consumer lenders. Two requests were handled:

1. A **Solutions page** following the structure in an attached wireframe doc
   (`Min-IT_Website (1).pdf`), taking inspiration from
   <https://easylodgesoftware.com.au/solutions/>.
2. Full copy for **five pages** — Solutions, Partners, Pricing, About Us, Contact —
   taking inspiration from <https://easylodgesoftware.com.au/>.

**Confirmed direction:**
- Deliver **in chat** (not as a file) unless asked otherwise.
- **AU-led** positioning. Compliance-led voice. US integrations noted as
  *in development* only — never shown as live.
- **Persona 2 (growing lenders)** is the centre of gravity for all copy.

---

## 2. Source material (in this folder)

| File | What it is |
|------|-----------|
| `Brand_QA.docx` | **Source of truth** for brand facts, voice, competitors, personas, market detail. |
| `Min-IT_Website (1).pdf` (uploaded) | Wireframe/structure doc for the main page (nav, hero, social proof, integrations, personas, product modules, application-to-repayment flow, why Min-IT, testimonials, CTA). |
| `minit_platform_flow_v4.html` | Interactive platform flow: LOS/CRM → Pay → LMS → Member Portal, with every stage/feature. |
| `minit_hero_animation.html` | Hero animation. |
| `CRM Field Setup _ Min-IT.pdf`, `screencapture-*` | Product screenshots / CRM reference (domain: `crm.min-it.co`). |

**Reference site studied:** Easylodge (easylodgesoftware.com.au) — solutions, partners,
pricing, about, contact pages all fetched and used as structural templates.

---

## 3. Key facts (from Brand_QA — use these, not Easylodge's)

- **Founded 2006**; 20+ years serving Australian lenders.
- **Brisbane HQ** (Eagle Street), distributed dev team. **11–25 staff.**
- **Bootstrapped / self-funded.** Independence is a positioning point.
- **150+ current clients** (Brand_QA says 50–150 customers; wireframe says 150+).
- **4.4M+ applications processed · AUD 12B+ processed.**
- **Go-live: 7–10 working days**, migration included.
- **Pricing:** flat platform access fee + per-contract usage fee. No per-seat.
- **Hosting:** Microsoft **Azure, AU region** (sandbox + prod), AU data residency.
- **Products:** Min-IT CRM (origination/LOS), Min-IT Pay (payments),
  Min-IT LMS (servicing), Member Portal. Plus e-contracts/e-sign, multi-channel comms.
- **AU integrations (live):** Equifax AU, Equifax ID Matrix, TaleFin, CreditSense,
  GBG GreenID, Zepto (NPP/BECS), GlobalPay, SendGrid, SMS gateway.
- **US integrations (in dev):** GoCardless/Usio/PayNearMe (payments), ValidiFI (bank
  verification), Accelitas/Zest AI/Equifax US (credit), Argyle (income/employment),
  Socure/Mitek (ID/KYC/fraud).
- **Compliance:** ASIC, NCCP, National Credit Code, ACL, Privacy Act 1988 / APPs,
  Credit Reporting Privacy Code, AUSTRAC/AML-CTF, AFCA. SOC 2 + ISO 27001 *in progress*.
- **Loan types:** SACC, MACC, consumer secured/unsecured, vehicle/asset finance,
  business/commercial lending, coded & non-coded products.
- **Clients (AU):** Cashlab, EFT & CashCow, Megacashgo. **(US):** Sunshine Loans, Enable Loans.
- **Competitors:** finPOWER (enterprise, established), BizCore (simple/cheap),
  Simpology, Aryza Lend, Salesforce FSC, in-house builds. Min-IT wins on flexibility,
  hands-on support, and being purpose-built for real lending ops. Loses on brand
  recognition and enterprise credentials/certs.

### Positioning guardrails
- Min-IT is **NOT** a neobank, BNPL platform, debt collector, generic CRM, accounting
  tool, payment processor only, broker aggregator, or credit bureau. It's the software
  lenders use to run their own operations.
- Don't overclaim on enterprise-bank transformation, global banking, advanced AI
  underwriting, or enterprise procurement credentials.

### Voice
Compliance-led, formal/regulatory, reassuring, audit-ready, trust-building over
technical, industry-fluent. Hero tagline pun: **"_Seriously_ Compliant Lending Software"**
(the wireframe's "Complaint" is a typo — intended word is "Compliant").

---

## 4. Open questions / to resolve

1. **Hosting conflict — Azure vs AWS.** Brand_QA says **Azure AU**; the wireframe doc's
   compliance line says **AWS**. All copy currently uses **Azure** (Brand_QA = source of
   truth). ⚠️ Confirm before publishing — appears on Pricing, About, Solutions.
2. **Contact page placeholders:** phone number, support email (guessed `hello@min-it.co`
   from CRM domain), full Brisbane address.
3. **Client testimonials:** logos + pull quotes for Cashlab, EFT & CashCow, Megacashgo
   still needed.
4. **Client count:** reconcile "50–150" (Brand_QA) vs "150+" (wireframe).

---

## 5. What's been produced

Delivered **in chat** across two turns:

- **Main / Solutions page (v1)** — full copy following the wireframe structure: Nav,
  Hero, Social Proof, Integrations, Built for Your Stage (3 personas), One Platform
  (4 product modules), Application-to-Repayment flow (Apply→Assess→Approve→Disburse→
  Service→Report), Why Min-IT, testimonials, Bottom CTA.
- **Five pages (Easylodge-modelled):**
  - **Solutions** — reframed by lender type (SACC/MACC, consumer, vehicle/asset,
    business/commercial, non-bank/specialist, credit reps) + loan types.
  - **Partners** — integrations embedded, AU live + US in-dev, open API.
  - **Pricing** — flat fee + usage, 3 packages (Servicer / Originator+Servicer /
    Advanced+Multi-product), always-included, FAQs.
  - **About Us** — founder/heritage story, by-the-numbers, values, what-we-don't-do,
    credentials.
  - **Contact** — support-led ("talk to the team that builds the platform"), get-in-
    touch, why clients stay, enquiry form, CTA.

_Full copy blocks live in the chat transcript for this session._

---

## 6. Suggested next steps

- Resolve the four open questions above.
- Package all pages into a single Word doc or CMS-ready markdown for handoff (offered).
- Draft remaining pages if needed (Home, How It Works / Platform, individual product pages).
- Optional: run copy through `humanizer` / `stop-slop` before publishing.
