# PayHaq — the full build log

This is the working record of what we thought, what we rejected, what we built, and why. It covers the CodeNexus India 2026 Round 1 submission by **Team Update** (Shikhar Goel and Ishpreet Singh, Thapar Institute of Engineering and Technology, Patiala).

---

## 1. Snapshot

| | |
|---|---|
| Event | CodeNexus India 2026 — National Hackathon, by WeCodeCoders on Unstop |
| Dates | 2–13 November 2026, completely online |
| Team size | 1–4; we are 2 |
| Round 1 | PDF submission, 2 Nov 10:00 → 3 Nov 18:00 IST |
| Round 1 field | 1,000+ teams; 300 go through to Round 2 |
| Track | Agentic AI |
| Round 2 | 4–7 Nov, 72 hours; functional product with a working central workflow |
| Round 3 | 10–13 Nov, 72 hours; top 100; ₹399 team fee if selected |
| Final judge | Inkloom |
| Prizes | ₹30,000 pool, paid internships, incubation, .xyz domains, AI credits, certificates |

The organiser's public event page listed the Round 1 sections and the 100-point rubric. That page became our specification.

---

## 2. Operating constraint: no official template

CodeNexus released the problem statement and the official PDF format through the official WhatsApp channel one hour before Round 1. The invite link had been reset, so we could not access the channel.

We did not stop. We reconstructed the requirements from:

- The organiser's public CodeNexus event page, which lists every Round 1 submission item and the scoring sheet.
- The Unstop competition and round metadata, which confirmed dates, team size, track names and the submission window.
- The published rubric: understanding of the problem (25), proposed solution (25), technical plan (20), originality (15), feasibility and scope (15).

Every page of the PDF maps to a scored criterion. If the official format arrives later, the content can be remapped without rewriting the substance.

---

## 3. How we read the brief

The rubric rewards a plan that is **specific**, **original**, **technically defensible** and **finishable**. It penalises scope that sounds impressive but cannot be built.

We therefore optimised for:

1. **A narrow user and a specific legal trigger** — not “AI for MSMEs.”
2. **A workflow that needs an agent** — multi-step, tool-using, with memory and human approval.
3. **A demo that can run in 72 hours** — a CSV ledger, a generated notice, a claim packet, a deployed dashboard.
4. **A hard part we can name and mitigate** — evidence reconciliation and legal accuracy.
5. **An original angle** — the evidence graph, not another chatbot.

Round 1 rules also mattered: the product must be built inside the hackathon window, significant AI tools must be disclosed, and every team member must file their own submission entry with their role and contribution.

---

## 4. Idea exploration

We considered several Agentic AI directions before choosing PayHaq.

| Idea | Why it was attractive | Why we did not choose it |
|---|---|---|
| **LabhAI** — agentic government-scheme navigator for MSMEs | Large unclaimed benefits; clear document workflow; strong social impact | Scheme rules are fragmented and change often; a credible demo depends on curating dozens of rules or stale portal data; the “scheme finder” space is crowded |
| **RTI Sahayak** — agentic RTI drafting and follow-up | Civic impact; clear legal workflow; feasible drafting demo | Filing depends on portal behaviour; a narrower buyer; harder to show a cash outcome in a 72-hour build |
| **QuotePilot** — agentic RFQ-to-quote for small manufacturers | Clear B2B ROI; document parsing; human approval | Less differentiated in a hackathon field; the emotional pull and measurable outcome are weaker than recovered cash |
| **Agent audit / red-team platform** | Technically strong; fits an AI-company judge | A developer tool, not an end-user product; harder to explain the impact in one page |
| **Generic “AI copilot for MSMEs”** | Easy to describe | It does not execute anything; fails the originality and solution criteria |
| **PayHaq** — agentic receivables recovery | Specific law, specific user, cash outcome, evidence-heavy workflow, demoable with a ledger | Chosen |

### Why PayHaq won

- **The trigger is unambiguous:** 45 days under Section 15 of the MSMED Act, 2006.
- **The number is defensible:** compound interest at 3× the RBI bank rate, monthly rests, under Section 16.
- **The user is specific:** a micro/small B2B supplier with 5–50 employees and no in-house finance or legal team.
- **The workflow is genuinely agentic:** reconcile → audit → draft → file → track, over weeks, with tools and human gates.
- **The demo is feasible:** upload a real-looking ledger, surface overdue invoices, generate a cited notice and claim packet, show the dashboard.
- **The outcome is cash, not a report.**

---

## 5. Legal research behind the plan

We built the plan around the Micro, Small and Medium Enterprises Development Act, 2006.

- **Section 15** — a buyer must pay a micro or small supplier on or before the agreed date; in no case may the agreed period exceed 45 days from acceptance or deemed acceptance.
- **Section 16** — if the buyer fails to pay, the buyer is liable to pay compound interest with monthly rests at three times the bank rate notified by the RBI.
- **Section 18** — a reference can be made to the Micro and Small Enterprises Facilitation Council (MSEFC) in the state.
- **MSME Samadhaan** — the online portal for filing delayed-payment applications.

We deliberately kept the scope to **B2B invoices from micro and small suppliers**. We are not claiming to cover medium enterprises, consumer debt, insolvency, arbitration strategy or legal representation.

The interest figures in the PDF are illustrative. The real engine must use the RBI bank rate notified on the relevant date, monthly compounding, and the exact invoice dates. The plan says this explicitly.

---

## 6. Users and workflow

### Primary persona

**Rakesh, 38** — owner of a precision components unit in Pune. 22 employees, ₹3.2Cr annual revenue, six active buyers, 60–120 day payment cycles, ₹38L overdue, no in-house finance or legal team. He knows who owes him. He does not have the time to chase legally, and he cannot afford to lose the buyer.

### Secondary persona

**Meera, 34** — a CA with 60 MSME clients. She wants a repeatable recovery workflow, not another inbox. She cannot chase for every client, but she sees advisory revenue in solving it.

### The workflow we designed

1. **Ingest & reconcile** — CSV/XLSX or Tally export; match invoices to payments and credit notes; flag partial and ambiguous matches.
2. **Detect & audit** — find invoices past 45 days for micro/small suppliers; build the evidence pack (PO, invoice, delivery challan, e-way bill, bank credit, correspondence); score completeness.
3. **Quantify & draft** — compute principal and statutory compound interest; draft a cited demand notice and Samadhaan claim; choose a relationship-preserving or firm tone.
4. **Approve & file** — the owner approves every notice and claim; send by email/registered post; prepare the Samadhaan packet.
5. **Track & recover** — follow-up cadence, response classification, escalation to the MSEFC, settlement tracking and a recovery dashboard.

### The agents

| Agent | Input | Output |
|---|---|---|
| Reconciler | Ledger, bank statement | Matched invoices, exceptions |
| Evidence Auditor | Invoice, PO, challan, e-way bill | Completeness score, missing-document list |
| Legal Drafter | Evidence pack, legal corpus | Cited notice + claim statement |
| Filing Agent | Approved packet | Sent notice / Samadhaan application |
| Tracker | Responses, deadlines | Next action, escalation, recovery status |

The human gates are: **approve notice**, **approve filing**, **approve settlement**. The agent never sends without a human yes.

---

## 7. Technical decisions

### Stack

- **Next.js + TypeScript + Tailwind + shadcn/ui** for the dashboard and document viewer.
- **FastAPI + Python 3.12** for the API, ledger parsing and document pipeline.
- **LangGraph + OpenAI GPT-4.1/4o** for the stateful agent workflow and structured outputs.
- **Postgres + pgvector** for cases, evidence and legal retrieval in one datastore.
- **Redis** for jobs, **S3** for documents, **React-PDF/WeasyPrint** for notices and claims.
- **Langfuse + Sentry** for tracing and failure detection.

### Why these choices

- **LangGraph, not a simple chain:** the workflow spans weeks, needs resumability, and has human-in-the-loop nodes. A chain is the wrong abstraction.
- **Deterministic interest engine, not LLM math:** legal arithmetic must be exact and testable. The LLM can explain the number; it cannot compute the number.
- **RAG with citations, not fine-tuning:** the law and portal guidance change; every claim needs a source and a last-verified date.
- **One Postgres + pgvector datastore:** fewer moving parts for a 72-hour build; the evidence graph and embeddings live together.
- **Mock filing in Round 2, live portal filing in Round 3:** de-risk the portal and keep the core workflow demoable.
- **Evidence graph as the moat:** the product’s trust comes from traceability, not from a better prompt.

### The hard part, named

**Evidence reconciliation and legal accuracy.** Partial payments, credit notes, multiple invoices per PO, scanned challans, and ambiguous matches can break a claim. Mitigations:

- Deterministic matching rules plus confidence scores.
- The user resolves ambiguous matches; the agent does not guess silently.
- Evidence completeness score before drafting.
- Section-cited legal RAG with a “no citation, no claim” guardrail.
- Human approval at every irreversible step.
- A 50-case evaluation harness with known ground truth.

---

## 8. Scope

### Round 2 — the MVP

- CSV/XLSX ledger ingestion (plus a Tally export shape).
- Reconciliation with exceptions.
- 45-day detection for micro/small suppliers.
- Deterministic statutory interest calculator.
- Evidence checklist and completeness score.
- Demand notice + claim statement PDF with citations.
- Pipeline dashboard, approval flow and audit log.
- Mock Samadhaan filing (downloadable packet).
- Deployed demo and a 3-minute walkthrough.

### Round 3 — the three named improvements

1. **Live Samadhaan filing** — Playwright automation with human confirmation and a downloadable fallback.
2. **Buyer correspondence agent** — email/WhatsApp follow-ups, response classification, settlement options, tone control.
3. **CA multi-client workspace** — portfolio view, bulk actions, client-level recovery reports.

### Out of scope, deliberately

Legal representation, consumer debt, lending, arbitration strategy, and recovery from insolvent buyers. Scope is a feature.

---

## 9. The PDF: structure and design

### Page map

| Page | Section | What it does |
|---|---|---|
| 1 | Cover | PayHaq, tagline, track, team, institution |
| 2 | Problem | 45-day rule, 3× interest, cost, existing tools, problem statement, scope, 45-day clock |
| 3 | Users | Rakesh persona, Meera persona, jobs-to-be-done, day-in-the-life, jobs-to-decisions map |
| 4 | Solution | One-liner, why an agent, before/after, differentiation, why now, product principles |
| 5 | Workflow | Five stages, agent roles, worked scenario, human gates, two tones |
| 6 | Features | MVP, three Round 3 improvements, post-event, product wireframe, 3-minute demo |
| 7 | Technical plan | Architecture, stack, interest engine, legal RAG, evidence graph, hardest problem, evaluation, latency, guardrails |
| 8 | Plan & impact | Three rounds, risks, target impact, post-event roadmap, 72-hour build sequence |
| 9 | Team | Profiles, certificate lines, why we win, Round 2 ownership, what we will show |

### Design system

- A4, 9 pages.
- Navy `#0B1F3A`, teal `#0E7C7B`, amber `#D98A2B`, warm paper `#FBFAF7`.
- Avenir Next / Helvetica Neue for sans, Georgia for editorial pull quotes, SF Mono for labels.
- Inline SVG diagrams: architecture, no external images, no stock photography.
- Consistent header/footer, page numbers, and a “takeaway” line on content pages.

### Build pipeline

1. One `index.html` with all content and CSS.
2. `@page { size: A4; margin: 0; }` plus fixed 210×297mm page sections.
3. Chrome headless `--print-to-pdf` with `--no-pdf-header-footer`.
4. PyMuPDF renders every page to PNG for visual QA.
5. Text extraction checks for key terms and inconsistencies.
6. Page count, file size and typography checks.

### A real bug we found and fixed

The first render produced **18 pages**: each A4 section was splitting into two because the print stylesheet had no `@page` rule, so Chrome applied default margins to a 297mm-tall section. Adding `@page { size: A4; margin: 0; }` produced the correct **9 pages**. This is why the QA step renders the actual PDF, not just the HTML.

### Content passes

- First pass: complete 9-page skeleton.
- Second pass: filled the bottom whitespace with substantive sections — the 45-day clock, jobs-to-decisions mapping, why now, tone samples, demo script, latency budget, guardrails, 72-hour build sequence, ownership table.
- Third pass: consistency fixes (“nine steps” → “five stages”; “Udyam trigger” → “Udyam evidence”) and a final text extraction check.

---

## 10. What we actually did, in order

1. Pulled the Unstop competition and round metadata to confirm dates, team size, tracks and the Round 1 window.
2. Read the organiser’s public CodeNexus page for the submission sections, rubric, rules and certificate policy.
3. Tried to recover the official problem statement and template; the WhatsApp invite had been reset, so we proceeded from the public requirements.
4. Explored four project directions; rejected scheme navigation, RTI filing and RFQ quoting for the reasons above.
5. Chose PayHaq and wrote the problem, personas, workflow, technical plan and scope.
6. Designed the 9-page PDF and wrote the full copy.
7. Built the HTML/CSS layout with inline SVG diagrams and a dashboard wireframe.
8. Rendered with Chrome headless, found the 18-page split, fixed the `@page` rule, and reached 9 pages.
9. QA’d every page visually, filled the whitespace with real content, and added the takeaway lines.
10. Published the PDF and source to GitHub; prepared the Unstop submission text for both team members.

---

## 11. Team roles

**Shikhar Goel — Product & AI Lead**  
Product research, agent orchestration, legal retrieval, statutory interest engine, evaluation.  
Certificate line: *Led product research and built the agent orchestration, legal retrieval and statutory interest engine.*

**Ishpreet Singh — Full-Stack & Design Lead**  
Next.js dashboard, document pipeline, deployment, UI/UX, demo.  
Certificate line: *Built the Next.js dashboard, document pipeline and deployment, and designed the end-to-end user experience.*

Both: integration, testing and submission. Every member files their own entry on Unstop.

---

## 12. Submission checklist

- [x] Final PDF: `PayHaq_Round1_TeamUpdate.pdf`, 9 pages, A4, ~823 KB.
- [x] Public PDF link.
- [x] Main Unstop submission text.
- [x] Shikhar’s role and contribution line.
- [x] Ishpreet’s role and contribution line.
- [ ] Both members submit their own Unstop entry.
- [ ] Screenshot each confirmation.
- [ ] Submit before 18:00 IST on 3 November.

---

## 13. What we would do next

- If the official brief or PDF template arrives, remap the same content into it without changing the substance.
- Have a lawyer review the notice/claim templates and the interest logic before any pilot.
- Build the 50-case evaluation set before Round 2 demo day.
- Pilot with one cluster association (Ludhiana, Pune, Coimbatore or Rajkot) after the hackathon.
- Expand from CSV to Tally/Zoho integrations, then TReDS/invoice financing.

---

## 14. Sources

- Unstop: CodeNexus India 2026 — National Hackathon, competition 1764747.
- WeCodeCoders: CodeNexus India 2026 event page, schedule, rules, rubric and certificate policy.
- The Micro, Small and Medium Enterprises Development Act, 2006 — Sections 15, 16 and 18.
- MSME Samadhaan portal.
- RBI bank rate notifications.

---

> PayHaq is a workflow and documentation tool, not a law firm. Legal rules and interest calculations should be verified with a qualified professional before use. The interest figures in the submission are illustrative, not a promise of recovery.
