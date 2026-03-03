# Founder Document Architecture v0.2
## Project: Vehicle Identity & Secondary Market Trust Layer

Purpose:
This document defines the internal documentation structure of the project.
It exists to ensure strategic coherence, structured iteration, and disciplined execution.

This is not an investor document.
This is not a marketing artifact.
This is the founder operating system.

---

# Document Hierarchy

All documents derive from the Context Pack.
The Context Pack is the source of truth.

Each document has a defined scope and must not overlap unnecessarily with others.

---

## 00 — Context Pack (Source of Truth)

Purpose:
Define the core thesis, architecture, positioning, and long-term ambition.

Contains:
- Core thesis
- Trust layer positioning
- Event model
- Node model
- DIY philosophy
- Verification coverage signal
- Official report endgame
- API-first future
- MVP scope
- North Star metrics

This document must remain stable and versioned.

---

## 01 — Vision & Thesis

Purpose:
Articulate why this company should exist.

Focus:
- Secondary market inefficiencies
- Information asymmetry
- Why service-layer verification matters
- Why now
- 5–10 year transformation narrative
- Market reframing

Not included:
- Technical details
- MVP specifics
- Implementation plans

---

## 02 — Incentive & Adoption Model

Purpose:
Validate behavioral feasibility.

Must answer:
- Why owners participate
- Why workshops participate
- Why institutional actors care
- What is the wedge
- Chicken & egg resolution
- Incentive alignment
- Friction analysis

This document determines viability.

---

## 03 — Signal & Trust Model

Purpose:
Define the economic meaning of the trust signal.

Must define:
- What the signal represents
- How verification coverage works conceptually
- How credibility gradients function
- How inspection reinforces DIY
- What strengthens or weakens signal integrity
- How signal becomes economically relevant
- Interpretability model (not UI)

This is the conceptual core of the product.

---

## 04 — Business Model & Monetization

Purpose:
Define revenue logic.

Must clarify:
- Primary payer(s)
- Revenue layer(s)
- Institutional API model
- Official report monetization
- Free vs paid layers
- Revenue progression over time

Must align with Incentive Model and Signal Model.

---

## 05 — Infra MVP PRD

Purpose:
Define the first build.

Must include:
- Entities
- Event proposal vs ledger model
- Signing flow
- Inspection linking
- Permissions
- Claim flow
- Basic verification coverage logic
- Workshop operational panel

Must not include:
- Advanced analytics
- Marketplace logic
- Long-term features

---

## 06 — 90-Day Validation Plan

Purpose:
Operationalize startup discipline.

Must include:
- Core hypotheses
- Experiments
- Metrics
- Validation thresholds
- Kill criteria
- Iteration cycles

This prevents idea drift.

---

## 07 — Long-Term Architecture (Future Phase)

Purpose:
Design scalability and defensibility.

Includes:
- API layer design
- Signal query model
- Official report standardization
- Risk scoring engine
- Data moat strategy
- Institutional integration roadmap

Only written after early validation.

---

# Context Dependencies

To ensure coherence, each document must be generated using only the relevant upstream documents.

## Vision & Thesis
Required context:
- context-pack.md
- document-architecture.md

## Incentive & Adoption Model
Required context:
- context-pack.md
- document-architecture.md
- vision-and-thesis.md

## Signal & Trust Model
Required context:
- context-pack.md
- document-architecture.md
- vision-and-thesis.md

## Business Model & Monetization
Required context:
- context-pack.md
- vision-and-thesis.md
- incentive-and-adoption-model.md
- signal-and-trust-model.md

## Infra MVP PRD
Required context:
- context-pack.md
- signal-and-trust-model.md
- incentive-and-adoption-model.md

## 90-Day Validation Plan
Required context:
- context-pack.md
- vision-and-thesis.md
- incentive-and-adoption-model.md
- signal-and-trust-model.md
- business-model-and-monetization.md

## Long-Term Architecture
Required context:
- All previous documents.

---

# Writing Discipline Rules

1. No document should redefine the thesis.
2. No document should overlap scope without reason.
3. Strategic changes must first update Context Pack.
4. MVP PRD must never drive strategy.
5. Signal integrity must remain non-negotiable.
6. Infrastructure serves signal, not vice versa.

---

Version: 0.2
Scope: Founder Internal Use