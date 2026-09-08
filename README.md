# BCS AI Workforce — Implementation Review

Evaluation of **BCS AI Workforce Implementation Manual v1.0** (draft, Sept 2026) against
the stated three-phase plan: ProposalApp marketing → demo → fulfillment, then BCS-CG
GovCon, then CMMC CISO work.

**Revision 2** — incorporates answers to the five open questions: 2–3 unique people per
program (internal and external, 6–9 total); BCS authors 80–90% ready proposal drafts and
syncs weekly with the client's proposal team; ProposalApp holds no CUI; CMMC delivered as
CISO/RP services with possible RPO registration, on separate tooling; ~$630/mo current
tool spend. Compliance and program claims verified against primary sources.

Full review: [`docs/ai-workforce-review.html`](docs/ai-workforce-review.html)

## Verdict

Architecturally sound, operationally too heavy for the team that has to run it.

**Keep as written:** the CUI/FCI prohibition list (specific enough to be testable), the
shared work record with structured handoffs instead of passing chat history between
models, the four-way separation of authority (draft / update internal / send external /
approve commitments), completion evidence on every A–Z step, and "human review time" as a
tracked measure.

**Fix before building:** nine named human roles still collapse per program and leave
self-approval intact — with three programs, cross-program review fixes this at no cost;
26 sequential gates put ~40–60 hours of governance labor before the first agent-produced
deliverable; the routing table assigns 7 model routes against volumes too small to tell
them apart.

**Biggest content gap:** demo and fulfillment — two-thirds of phase-one scope — are absent
from the manual. Confirming that BCS authors 80–90% of client proposal drafts makes this
the centre of the programme, not an edge omission. Needs a three-class data model
(public / NDA-business / restricted) rather than a blanket prohibition. Good news on
scope: FCI is *information provided by or generated for the Government under a contract*,
so most pre-award proposal work is a contractual confidentiality duty, not a regulatory
one. The narrow exception to target is past-performance and incumbent-recompete material.

**New findings from the answers:**
- **Nothing currently paid for can run the automation.** ChatGPT Pro, Claude Max and Claude
  Team seats are human-interface subscriptions, not programmatic access. Hermes/Composio
  need API credentials billed by usage — a new line item, estimated ~$150–300/mo at the
  stated volumes, dominated by research. Model spend is *not* where the money goes; seats
  and CRM tiering are.
- **External personnel have no access policy.** NDAs before access, named identities,
  per-program scoping, 24-hour offboarding revocation, client consent to subcontractors,
  and verified RP credentials for CMMC advisory.
- **Personal Gemini/Perplexity accounts hold business data.** No admin control, no audit,
  consumer retention terms, nothing to revoke at offboarding — the exact finding BCS would
  write up in a client readiness assessment.
- **SalesRobot + 2 LinkedIn accounts is live ToS-violating automation.** Standard
  consequence is account restriction. Make it a recorded decision, not a default.
- **CMMC Phase II was suspended 13 July 2026** (Level 2 third-party assessments, due to
  start 10 Nov 2026); a reform task force is reviewing the program. Phase I is untouched —
  self-assessments, DFARS 252.204-7012, NIST SP 800-171, SPRS posting and annual
  affirmations all continue. Agent-drafted CMMC content built from pre-July sources will
  confidently state a suspended requirement. Needs a volatile-claims register and a
  source-recency rule, not just "every fact needs a source".

**Reframe worth making in sales, not just in the manual:** under CMMC, an external service
provider is in assessment scope when it processes, stores or transmits CUI on a client's
behalf; a cleanly scoped advisory relationship that never receives CUI generally does not
make the advisor an ESP. The Tier 3 boundary is therefore a business asset — it keeps BCS
off the assessment path and cheaper to engage. RPOs advise and do not assess, so the
RP/RPO positioning carries no C3PAO independence conflict.

## Delegation summary

| Tier | Rule | Examples |
|---|---|---|
| 1 — delegate now | Recurring, reversible, rubric-governed, public data only | Account research → sourced brief; ICP scoring; **compliance matrix from Sections L/M**; solicitation & amendment watch; outreach drafting (no send authority); reply triage; demo/meeting briefs; demo recaps; format & page-limit QA; weekly client sync package; CRM hygiene; CMMC education content; intake status tracking; scorecard assembly |
| 2 — agent assists, human authors | Judgment-bearing or NDA-scope client data | Proposal narrative from approved boilerplate; past-performance library (written releases only); pricing narrative structure (never numbers); teaming shortlists; demo script tailoring; CMMC policy templates on synthetic data; evidence *request* lists |
| 3 — human only, no agent involvement | Irreversible, professionally attributable, or CUI/FCI | Bid/no-bid, pricing, terms, reps & certs, submission; CMMC scoping and assessment conclusions; SSP/POA&M authorship and evidence handling; anything touching CUI/FCI/credentials; fractional CISO advisory judgment; first substantive reply to a live buyer |

**Estimated net effect** (assumption pending a measured baseline): ~43 h/week gross across
all three phases, less 8–10 h/week agent supervision overhead → **~33–35 h/week net**, just
under one FTE. Phase one alone: 23–29 h/week net, concentrated almost entirely in two
capabilities — research-to-brief and compliance-matrix construction. If those two work, the
programme works.

## Recommended resequencing

Three distinct teams changed the constraint: it is no longer team capacity but the single
shared **PLATFORM** role (agent config, evals, access, model routing, change control).
Don't triplicate it — configurations drift apart.

1. **Days 1–3 — thin slice.** One task type (research → brief), spreadsheet work record,
   approvals in an existing channel, no runtime, no OAuth gateway, no charter. Five real
   accounts. Doubles as the quantified baseline the manual's step B needs.
2. **Weeks 1–4 — Wave 1.** ProposalApp marketing, human-triggered (steps A, C, D, E, K, N,
   F, L). In parallel at no platform cost: BCS-CG builds domain knowledge; CMMC builds the
   volatile-claims register and verified education content.
3. **Weeks 5–10 — Wave 2.** Write the missing demo and fulfillment procedures. Build the
   compliance-matrix skill domain-independent so BCS-CG inherits it. Add runtime + OAuth
   gateway now. Define and test emergency stop.
4. **Weeks 8–14 — Wave 3.** BCS-CG activation as a knowledge swap. Can start before Wave 2
   closes since the team is distinct.
5. **Weeks 8–16 — Wave 4.** CMMC Growth marketing layer; delivery stays human-only.

**Revised overlap rule:** a new program activates when PLATFORM has closed the prior
program's open defects — not when the prior team is free. Domain knowledge work never
waits; only agent activation does.

**Governance:** four roles, not nine — one SPONSOR (firm-wide), one PLATFORM (shared), three
PROGRAM LEADs. Security review is assigned to a program lead from a *different* program,
never to PLATFORM.

## Budget

Current ≈$630/mo across 8 vendors. Incremental for the agent workforce ≈$150–300/mo in API
usage plus Hermes/Composio subscriptions. Recommended explicit ceiling: **$1,000/mo through
Wave 2**, revisited at the Wave 3 gate. The forecastable step change is HubSpot tiering and
seats at 6–9 users across three pipelines — not models.

## Decisions the answers created

1. Are the LinkedIn accounts disposable? (If not: agent-drafted, human-sent — you keep
   nearly all the time saving, since drafting is where the hours are.)
2. Who is the single PLATFORM owner, and do they have capacity for three programs?
3. Should CMMC move ahead of BCS-CG, given the suspension improved the fit with the
   advisory positioning?
4. What is the standing FCI determination process per engagement?
5. Which model vendors survive consolidation? (Personal accounts go regardless.)
