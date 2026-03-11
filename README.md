# Vehicle Identity & Secondary Market Trust Layer

Internal documentation for a vehicle identity and verification infrastructure designed to become a recognized trust signal in the secondary automotive market.

---

## Documents

Read in the following order:

### 1. [Vision & Thesis](vision-and-thesis.md)
Why this company should exist. Frames the secondary market's information asymmetry problem, explains why service-layer verification is the right approach, and lays out the long-term transformation narrative.

### 2. [Incentive & Adoption Model](incentive-and-adoption-model.md)
Will the relevant actors actually participate? Analyzes behavioral feasibility across owners, workshops, and institutional actors — mapping incentives, friction points, and the cold-start problem.

### 3. [Signal & Trust Model](signal-and-trust-model.md)
What the trust signal is and how it works. Defines Verification Coverage, credibility gradients, how execution and inspection events reinforce the signal, and what makes it economically meaningful.

### 4. [Business Model & Monetization](business-model-and-monetization.md)
Revenue logic derived from the thesis, incentive model, and signal model. Covers who pays, in what form, and how monetization evolves from operational tooling to institutional data access.

### 5. [90-Day Validation Plan](90-day-validation-plan.md)
Operationalizes startup discipline. Lists core hypotheses, experiments, validation thresholds, and kill criteria to test behavioral assumptions before committing to full infrastructure.

### 6. [One-Pager](one-pager.md)
A concise overview of the problem, solution, and opportunity — intended for co-founders, investors, and strategic partners.

### Superseded

- **[Infra MVP PRD](infra-mvp-prd.md)** — Original workshop-first MVP design. Superseded by the verifier-first PRD. Retained as architectural reference — the core entity model, event architecture, and signal integrity constraints informed the current build spec.

---

## Working Documents

### Verifier-First MVP

- **[Context](work/verifiers/context.md)** — Critical re-evaluation of the original MVP approach. Documents the pivot from a workshop-first infrastructure build to a verifier-first strategy, including rationale, flywheel mechanics, 10 open challenges with candidate solutions, and adapted validation plan.
- **[Decisions](work/verifiers/decisions.md)** — Resolved positions for each challenge. What gets built, what is deferred, and what must be validated. Living document, updated as decisions are made.
- **[PRD](work/verifiers/prd.md)** — Product Requirements Document for the verifier-first MVP. Defines the system architecture (Event-based ledger with detail tables per type, N:N user-node model), data entities, features by actor, principal flows, explicit exclusions, success metrics, and technical considerations. This is the actionable build spec.
- **[Ideas](work/ideas.md)** — Explorations and hypotheses requiring further validation before committing to the roadmap.

### Pitches

- **[Co-founders & Investors — EN](pitches/cofounders-investors-en.md)** | **[ES](pitches/cofounders-investors-es.md)** — 30-second and 60-second elevator pitches for early-stage conversations.
- **[Inspectors — EN](pitches/inspectors-en.md)** | **[ES](pitches/inspectors-es.md)** — 30-second and 60-second pitches for Phase 1 inspector outreach.
