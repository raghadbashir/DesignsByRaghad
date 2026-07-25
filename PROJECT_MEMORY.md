# DesignsByRaghad — Odoo Demo Project — Memory

Last updated: 25 July 2026. Read this first in any new chat to pick up where things left off.

## Who this is for
Raghad — a freelance graphic designer (brand: **DesignsByRaghad**) doing a 3-month internship at Streamline, building an Odoo demo of her real freelance business for presentation to employees/PMs.

## Documents already created (in the connected folder)
- **Part1_BusinessCase_Odoo.docx** — the main demo write-up, styled after a colleague's "Demo Business Case Proposal" format (Business Case → Problems/Requirements → Proposed Solution steps → Modules Used → Benefits → Future Work). Written in first person as Raghad, a freelancer (not a company). Deposit sequencing, WhatsApp/DM manual-lead handling, lead→customer conversion, and hourly-deposit reconciliation were all corrected per expert review.
- **Part1_UseCase.docx** — an earlier, more detailed narrative version (problem/why-it-needs-fixing/what-Odoo-offers/business-logic/workflow/future-work format). Revisions were removed from Part 1 scope (moved to Part 2 future work) since in Part 1 they happen outside Odoo.
- **Odoo_Import_Pack.xlsx** — ready-to-fill import workbook (Contacts, Products, CRM Leads, Sales Orders, Projects & Tasks, Timesheets, Invoices) with a Read Me tab. NOT yet used — importing was deprioritized in favor of building the demo live in Odoo instead.
- **DesignsByRaghad_Odoo_Demo_BuildLog.docx** — the detailed step-by-step build log (plain English, What/How/Why for each step) of the actual Odoo trial database build. This is the most important document for continuing tomorrow — read it fully.

## Two-part demo structure
- **Part 1 (in progress/built)**: login-free flow for short-term clients — CRM → Survey questionnaire → Quotation → Deposit → Project → Timesheets → Invoice → Payment. No client portal login.
- **Part 2 (not started, future work)**: portal-based flow for long-term/retainer clients — client login, in-system interactive revisions, milestone billing, contracts, deliverable library.

## The portfolio website (real, deployed)
- Real HTML/CSS/JS portfolio site located in this same connected folder (`index.html`, `styles.css`, `images/`, etc.), originally 736MB, compressed down to ~13MB deployable (originals kept safe in `originals_backup/`, excluded via `.gitignore`).
- Fixed: mobile viewport, nav anchors (#hero, #contact, #packages-section), header moved inside `<body>`, social preview meta tags added, hero background image (was CSS-only, got missed by first cleanup, then fixed).
- **Deployed live on GitHub Pages**: https://raghadbashir.github.io/DesignsByRaghad/
- The site's contact button ("ابدأ مشروعك") is wired to the Odoo web form with UTM tracking: `https://edu-slt.odoo.com/services?utm_source=portfolio&utm_medium=website`.
- Workflow for future edits: edit files in the connected folder → commit & push via GitHub Desktop → Pages rebuilds automatically in ~1-2 min.

## The Odoo trial database (this is Raghad's own database, not shared)
- URL: `edu-slt.odoo.com` — a personal Odoo trial from the Streamline internship (NOT a shared/classmate database — this was a false assumption corrected mid-project).
- Comes preloaded with Odoo's own sample/demo data (irrelevant products like Chips/Drones, extra companies like "Transfers") — this is normal trial noise, not real data to worry about.
- **Company set up**: DesignsByRaghad is the one true company; keep only it selected in the top-right company switcher to avoid seeing sample-data noise.
- **Foundation settings turned on**: Units of Measure (Sales settings) and Timesheets (Project settings).
- **Products created**: "Design — Hourly" (Service, Invoicing Policy = Based on Timesheets, Unit = Hours, Create on Order = Project & Task) and "Design — Fixed Package" (Service, Invoicing Policy = Prepaid/Fixed Price, Unit = Units, Create on Order = Project & Task).
- **CRM**: Leads feature turned on (Settings → CRM). A manual lead was created (Bless Cafe & Gelato — Brand Identity) to represent a WhatsApp/DM-style inquiry, then converted to an opportunity + customer.
- **Survey**: Client Intake questionnaire rebuilt in the Survey app from Raghad's real Google Form (all ~25 questions transcribed, grouped into 6 sections — full list is in the chat history if needed again). Survey link was sent to the lead manually (automation was considered but skipped — manual sending is normal for a solo freelancer).
- **Website contact form**: A clean form-only page built at `edu-slt.odoo.com/services` (NOT named "start a project" — actual slug is `/services`), Action = "Create a Lead", published. Four UTM-tagged versions of the link exist for tracking lead source: instagram, facebook, behance, portfolio (each `?utm_source=...&utm_medium=...`). Tested and confirmed working — Source field auto-populates on new leads.
- **Accounting fix**: New company had no Sales journal by default — fixed via Invoicing → Configuration → Settings → Fiscal Localization (set a basic chart of accounts), which created the missing journal.
- **Employee record**: Created "Raghad" as an Employee (linked to her own user login) — required because Timesheets needs an employee owner even for a one-person business.

## Working demo flow status (as of end of this session)
- ✅ **Hourly branch — fully complete end to end**: Order S00028 (Design — Hourly, client "hidaya") → project + task auto-created → timesheets logged (5 hours) → invoice generated from timesheets (INV/2026/00004) → a small existing down payment ($7) was automatically deducted → invoice confirmed and marked Paid ($168 due, paid). This proves the full "based on timesheets" flow works correctly.
- ⚠️ **Fixed-price + deposit branch — needs finishing**: The Bless Cafe & Gelato order originally had the WRONG product on it (a pre-existing demo product, not "Design — Fixed Package"), so no project got created. Fix identified but not yet confirmed complete: remove the wrong order line, add "Design — Fixed Package" instead, re-save/confirm, verify a project now appears, then redo the 30% down payment (Create Invoice → Down Payment percentage → 30 → Confirm → Register Payment), then eventually deliver + final invoice (bills fixed price minus deposit).

## Key corrected business logic (already fixed in the docs, keep consistent)
- Deposit sequence: questionnaire → quotation sent → **client accepts (confirms the order)** → THEN down payment is generated from the confirmed order. Never invoice a deposit before acceptance.
- WhatsApp/Instagram DM leads are added manually — not automatically captured. Only the Odoo web form (via tagged links) captures leads automatically.
- A CRM lead has no customer until converted to an opportunity (Convert to Opportunity → Create a new customer) — a quotation cannot be placed on a raw lead.
- On hourly projects, the deposit is a percentage of the *estimated* hours; the final invoice reconciles it against actual logged hours (small credit if work comes in under estimate) — confirmed working in the live demo (S00028 example).
- Revisions in Part 1 happen outside Odoo (WhatsApp/email/phone) and are NOT logged as Odoo tasks in Part 1 — full in-system interactive revision handling is Part 2 future work only.

## Immediate next steps for tomorrow
1. Finish the Bless Cafe fixed-price branch (see "Fixed-price + deposit branch" above).
2. Once both branches are fully complete, consider: customizing CRM stages and Project views/templates to better match Raghad's actual design workflow (mentioned as a future customization goal, not yet started).
3. Eventually build out Part 2 (portal-based long-term client flow) as its own use case document, following the same problem/solution + build-log approach used here.
4. Keep updating DesignsByRaghad_Odoo_Demo_BuildLog.docx step-by-step as new Odoo work happens — that's the running source of truth for what's been built and why.

## Working style notes
- User prefers concise, direct responses — minimal formatting, no unnecessary explanation.
- Build log document must stay in plain, simple English with What/How/Why for every step — no jargon, no over-complication.
- Always verify screenshots carefully before confirming a step is correct — several issues were caught this way (wrong product on an order, missing journal, blocked popups, missing employee record).
