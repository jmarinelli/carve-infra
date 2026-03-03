# Context Pack v0.3
## Project: Vehicle Identity & Secondary Market Trust Layer (Working Name)

---

# 1. Core Thesis

We are building a vehicle identity and verification infrastructure designed to become a recognized trust signal in the secondary automotive market.

The system’s purpose is to transform fragmented service history into a structured, progressively validated, and economically meaningful signal that increases confidence, reduces asymmetry, and enables value differentiation.

This is not a social network.
This is not a generic workshop SaaS.
This is not a listing marketplace.

This is a trust layer built from the service layer up.

---

# 2. Strategic Positioning

We are building:

- A vehicle identity ledger.
- A structured execution + inspection event model.
- A node-based signing system.
- A verification coverage signal.
- A future official report standard.

Long-term ambition:

> To become a recognized secondary-market trust signal for vehicles.

If successful, a vehicle’s verified history becomes economically relevant in resale, underwriting, and risk assessment contexts.

---

# 3. The Product Is the Signal

The core product is not the dashboard.

The core product is:

> A credible, interpretable, economically meaningful trust signal attached to a VIN.

This signal must:

- Be understandable by non-technical users.
- Be difficult to manipulate.
- Be progressively strengthened over time.
- Be verifiable independently.
- Be usable in transaction contexts.

Verification Coverage and structured history are components of this signal.

---

# 4. Architectural Principles

## 4.1 Vehicle-Centric Model

The vehicle is the primary entity.

Users, workshops, and future institutional actors interact with the vehicle identity layer.

VIN-based vehicle creation must be supported, including unclaimed vehicles.

---

## 4.2 Event Proposal vs Ledger Event

We explicitly separate:

### Event Proposal Layer
- Created by Owner or Node.
- Structured but not authoritative.
- Editable until signed.

### Ledger Event Layer
- Created only when signed by a verified node.
- Immutable.
- Corrections require new events referencing the original.

Owners:
- May create proposals.
- May not sign events.
- May not modify signed ledger entries.

Nodes:
- May create proposals.
- May sign execution events they performed.
- May create and sign inspection events.

Signing authority belongs exclusively to verified nodes.

---

## 4.3 Immutable Ledger

- Verified ledger events are immutable.
- No deletion of signed history.
- All corrections are additive.
- Signature is required for authoritative status.

---

# 5. Event Model

Events are first-class entities.

## 5.1 Execution Events

Represent work performed.

Examples:
- Maintenance
- Repair
- Modification

Execution actor:
- Owner (DIY)
- Workshop (Professional)

Execution mode must be explicit.

---

## 5.2 Inspection / Measurement Events

Inspection is a first-class event type.

Examples:
- Suspension inspection
- Pre-purchase inspection
- Alignment report
- Dyno measurement
- Safety check

Inspection events:
- Are always node-signed.
- Represent observed state at a specific time and odometer.
- May optionally link to execution events.

Inspection validates condition, not authorship.

---

# 6. DIY Philosophy

DIY is supported and respected.

DIY execution events:
- Start as owner-reported proposals.
- May remain unvalidated.
- May be reinforced by subsequent inspection events.

The system creates a credibility gradient:

- Owner Reported
- DIY + Inspection
- Professional Execution by Node

Transparency is rewarded.

---

# 7. Node Model

Nodes are verified entities authorized to sign ledger events.

Initial node type:
- Workshops

Future-ready:
- Inspection centers
- Insurance entities
- Measurement providers

Nodes may:
- Create VIN-based vehicles.
- Create and sign execution events.
- Create and sign inspection events.

Nodes may not modify signed ledger history.

---

# 8. Verification Coverage Signal

Each vehicle has a visible Verification Coverage metric.

Coverage measures:

- Kilometer continuity validated by signed events.
- Proportion of lifecycle verified.
- Structural consistency of event timeline.

Coverage is not cosmetic.
It is intended to evolve into an economically meaningful signal.

Owner-reported events carry limited weight.
Node-signed events carry full weight.

---

# 9. Official Vehicle Report (Endgame)

The system aspires to produce a standardized, timestamped, verifiable Official Vehicle Report.

This report represents:

- A snapshot of the vehicle’s verified state.
- Structured historical summary.
- Validation coverage.
- Flagged inconsistencies.
- Signed authenticity.

This report is intended to be usable in:

- Secondary market transactions.
- Institutional review processes.
- Risk evaluation contexts.
- Formal due diligence.

The report is distinct from API-based access.
It is a formal artifact.

---

# 10. API-First Future

Beyond consumer dashboards, the system is designed to support:

- VIN-based lookup access.
- Programmatic verification queries.
- Risk and anomaly signals.
- Institutional integrations.

The long-term payer is likely institutional actors requiring structured, scalable access to the trust signal.

Owners retain control over their vehicle identity visibility.
Signal-level access and bulk integrations are monetizable layers.

---

# 11. Workshop Incentive Model (Initial Hypothesis)

Workshops adopt the system because it provides:

- A job registry + certificate engine.
- Professional digital service certification.
- Exportable, verifiable records.
- Protection in disputes.
- Structured operational history.

This is not a full CRM.
It is a structured service record layer.

Marketplace lead generation is not the initial hook.

---

# 12. MVP Scope (Infra-First)

The first MVP focuses on:

- VIN-based vehicle creation.
- Owner claim flow.
- Event proposal creation.
- Node signing flow.
- Inspection events.
- Public verification page.
- Basic verification coverage signal.
- Simple workshop operational panel.

No marketplace.
No social features.
No advanced analytics.

---

# 13. North Star

Primary metric:

> Node-signed ledger events per month.

Secondary metric:

> Average verification coverage per active vehicle.

Long-term metric:

> Percentage of secondary market listings referencing the trust signal.

---

# 14. What This Is Not

- Not a social network.
- Not a pure listing platform.
- Not a generic workshop SaaS.
- Not AI-first.
- Not blockchain-first.

---

Version: 0.3  
Positioning: Secondary market trust layer with infrastructure foundation  
Trajectory: Build signal → Establish recognition → Enable institutional integration