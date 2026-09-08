# BCS AI Workforce — Implementation Review

Evaluation of **BCS AI Workforce Implementation Manual v1.0** (draft, Sept 2026) against
the stated three-phase plan: ProposalApp marketing → demo → fulfillment, then BCS-CG
GovCon, then CMMC CISO work — staffed at 2–3 co-workers plus agents per project.

Full review: [`docs/ai-workforce-review.html`](docs/ai-workforce-review.html)

## Verdict

Architecturally sound, operationally too heavy for the team that has to run it.

**Keep as written:** the CUI/FCI prohibition list (specific enough to be testable), the
shared work record with structured handoffs instead of passing chat history between
models, the four-way separation of authority (draft / update internal / send external /
approve commitments), completion evidence on every A–Z step, and "human review time" as a
tracked measure.

**Fix before building:** nine named human roles collapsing onto 2–3 people destroys
separation of duties; 26 sequential gates put ~40–60 hours of governance labor before the
first agent-produced deliverable; the 13-system stack and 7-route model table carry cost
against pilot volumes too small to measure.

**Biggest content gap:** demo and fulfillment — two-thirds of the stated phase-one scope —
are absent from the manual, and fulfillment is where the delegation return lives. Writing
that section exposes an unresolved contradiction: agents are forbidden sensitive data, yet
white-glove proposal production is the deliverable. Needs a tiered data model (public /
NDA-business / restricted), not a blanket prohibition.

## Delegation summary

| Tier | Rule | Examples |
|---|---|---|
| 1 — delegate now | Recurring, reversible, rubric-governed, public data only | Account research → sourced brief; ICP scoring; **compliance matrix from Sections L/M**; solicitation & amendment watch; outreach drafting (no send authority); reply triage; demo/meeting briefs; format & page-limit QA; CRM hygiene; CMMC education content; intake status tracking; scorecard assembly |
| 2 — agent assists, human authors | Judgment-bearing or NDA-scope client data | Proposal narrative from approved boilerplate; past-performance library (written releases only); pricing narrative structure (never numbers); teaming shortlists; demo script tailoring; CMMC policy templates on synthetic data; evidence *request* lists |
| 3 — human only, no agent involvement | Irreversible, professionally attributable, or CUI/FCI | Bid/no-bid, pricing, terms, reps & certs, submission; CMMC scoping and assessment conclusions; SSP/POA&M authorship and evidence handling; anything touching CUI/FCI/credentials; fractional CISO advisory judgment; first substantive reply to a live buyer |

**Estimated net effect** (assumption pending a measured baseline): ~43 h/week gross across
all three phases, less 8–10 h/week agent supervision overhead → **~33–35 h/week net**, just
under one FTE. Phase one alone: 23–29 h/week net, concentrated almost entirely in two
capabilities — research-to-brief and compliance-matrix construction. If those two work, the
programme works.

## Recommended resequencing

1. **Days 1–3 — thin slice.** One task type (research → brief), spreadsheet work record,
   approvals in an existing channel, no runtime, no OAuth gateway, no charter. Five real
   accounts. Doubles as the quantified baseline the manual's step B needs.
2. **Weeks 1–4 — Wave 1.** ProposalApp marketing, human-triggered. Steps A, C, D, E, K, N,
   F, L in that order. GitHub from day one; defer the persistent runtime and OAuth gateway
   until unattended writes actually exist.
3. **Weeks 5–10 — Wave 2.** Write the missing demo and fulfillment procedures. Build the
   compliance-matrix skill domain-independent so BCS-CG inherits it. Add runtime + OAuth
   gateway now. Define and test emergency stop.
4. **Weeks 11–16 — Wave 3.** BCS-CG activation as a knowledge swap, not a rebuild.
5. **Week 17+ — Wave 4.** CMMC Growth marketing layer only; delivery stays human-only.

**Overlap rule:** a new domain activates only after the prior domain meets its defect-rate
and human-review-time targets for three consecutive weeks, or a named additional owner
takes it.

## Open questions blocking a final draft

1. Are the 2–3 co-workers the same people across all three phases, or distinct?
2. Does ProposalApp white-glove mean BCS staff produce proposal content for clients?
3. Does ProposalApp (the product) store client proposal data?
4. Which CMMC role does BCS hold or intend to hold — consultancy, registered provider, or
   assessor? (Independence constraints differ.)
5. What is the actual combined monthly ceiling for tools and model usage?
