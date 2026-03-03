# 03 — Signal & Trust Model
## Vehicle Identity & Secondary Market Trust Layer

- Purpose: Define the economic meaning and structural behavior of the trust signal.
- Scope: What the signal represents, how Verification Coverage works conceptually, how credibility gradients function, how execution and inspection reinforce the signal, what strengthens or weakens it, and how it becomes economically relevant in the secondary market.

---

## 1. What the Trust Signal Is

The Trust Signal is not a score.
It is not a badge.
It is not a rating.

The Trust Signal is a structured representation of a vehicle's verified lifecycle — expressed in a form that is interpretable, difficult to manipulate, and progressively strengthened through verified service events.

Its fundamental property is this:

> The Trust Signal encodes how much of a vehicle's operational history has been validated by verified nodes, and how continuous and structurally consistent that history is.

It derives its meaning not from what it claims, but from what has been independently signed.

The signal exists at the vehicle level.
It is attached to a VIN.
It persists across ownership.
It strengthens over time — or reveals gaps.

It is:
- A measure of verifiable lifecycle continuity.
- A signal of documented stewardship and observed condition.
- A quantifiable reduction of information asymmetry.

The signal is the product.

---

## 2. What the Signal Represents Economically

In any asset market, price is a function of perceived value under uncertainty.

When information about asset condition is unreliable, buyers apply an uncertainty discount.
When sellers cannot credibly communicate condition, they are systematically under-rewarded for quality.
The result is a structural compression of price differentiation — well-maintained vehicles and poorly-maintained vehicles converge toward the same price band.

The Trust Signal exists to reduce this compression.

### 2.1 Reduction of Uncertainty Discount

Verification Coverage and signed history reduce uncertainty by:

- Increasing visibility of lifecycle events.
- Structuring maintenance continuity.
- Exposing condition observations.
- Making omissions more difficult.

The signal does not increase intrinsic mechanical value.
It reduces uncertainty around that value.

When the signal is strong:
- Buyers assume less risk.
- Sellers can differentiate credibly.
- The uncertainty discount diminishes.
- Price becomes a more accurate reflection of actual condition and stewardship.

When the signal is absent or weak:
- Buyers default to skepticism.
- Sellers of quality vehicles cannot distinguish themselves from sellers of poor-quality vehicles.
- The market operates with structural opacity.

That reduction can translate into:

- Higher clearing prices.
- Faster transaction velocity.
- Lower negotiation friction.
- More precise risk pricing.

---

### 2.2 Conversion of Invisible Effort into Legible Capital

Maintenance and professional work already occur.

Without structure, they produce limited economic differentiation.

The Trust Signal converts:

- Stewardship → visible continuity.
- Professional execution → portable proof.
- Inspection observations → condition evidence.

It transforms invisible effort into economically legible capital.

The signal's economic function is to make mechanical stewardship legible at the point of transaction — and beyond.

---

### 2.3 Risk Stratification

Over time, vehicles become segmentable not only by brand and mileage, but by lifecycle integrity.

The signal enables stratification across:

- Low visibility / fragmented history.
- Partially verified continuity.
- High verification coverage with inspection reinforcement.

This allows more granular risk modeling by dealers, insurers, financiers, and any institutional actor pricing vehicle risk.

---

## 3. Verification Coverage: Conceptual Model

Verification Coverage is the primary expression of the Trust Signal.

It is not a simple percentage.
It is a composite measure of structural quality across the vehicle's verifiable lifecycle.

### 3.1 What Coverage Measures

Verification Coverage captures:

**Kilometer continuity**
The degree to which signed events account for the vehicle's mileage progression without unexplained gaps. A vehicle with consistent, chronologically coherent signed events across its odometer range has high continuity. Gaps in kilometer coverage reduce the signal's integrity.

**Proportion of lifecycle verified**
The fraction of the vehicle's operational existence that has been touched by node-signed events. A vehicle with 8 years of history and 6 years of structured, signed events has higher coverage than one with only episodic documentation.

**Structural consistency of the event timeline**
Whether the event sequence is coherent: dates, odometer readings, event types, and reported conditions must form a logically consistent narrative. Inconsistencies — contradictions in odometer readings, implausible event sequences, unexplained state changes — reduce structural consistency.

### 3.2 Coverage as Continuity, Not Quantity

More events do not automatically mean stronger signal.

Coverage increases when:

- Signed events anchor specific mileage points.
- There is consistent progression without unexplained gaps.
- Inspections confirm state at defined intervals.

The emphasis is on continuity and structural coherence.

### 3.3 Coverage Is a Reflection, Not a Construction

Coverage cannot be manufactured retroactively.
It cannot be improved by adding unverified claims.
It can only grow through genuine, forward-time node-signed events.

This is what makes it a durable signal: it is anchored in real execution history, not in self-reported narrative.

---

## 4. Progressive Credibility: How the Signal Strengthens Over Time

The system intentionally avoids binary trust.
Instead, it constructs credibility gradients.

The signal is not binary.
It does not exist fully or not at all.
It accumulates.

### 4.1 Credibility Is Cumulative

Each node-signed event adds a verified data point to the vehicle's identity.

Over time, a vehicle with consistent, node-signed history develops:
- Higher kilometer continuity.
- Broader lifecycle coverage.
- Greater structural consistency.

The signal becomes harder to dispute — and more valuable as a trust anchor.

### 4.2 The Credibility Gradient

Not all events carry equal weight. A graduated credibility model applies:

| Level | Source | Weight |
|---|---|---|
| Owner-reported | Unverified proposal | Low |
| DIY + Inspection | Owner-reported, subsequently validated by inspection | Medium |
| Professional execution by Node | Signed execution event | High |
| Inspection event by Node | Signed inspection, independent of execution | High |

An owner reporting their own oil change carries limited credibility on its own.
The same event, followed by a node-signed inspection that confirms the expected mechanical state, carries substantially more.

Credibility is not only about who performed the work.
It is about what has been independently observed and signed.

Coverage strength derives from:

- Who signed.
- What was observed.
- How consistently the lifecycle is represented.

### 4.3 Retroactive Weakness

Gaps in history do not disappear with new events.
If a vehicle has 5 years of undocumented history followed by 2 years of strong verified coverage, the signal reflects both.

The signal is honest.
It does not reward selective documentation.

---

## 5. Execution and Inspection Events: Complementary Signal Inputs

The signal is built from two distinct event types that serve complementary functions.

### 5.1 Execution Events

Execution events represent work performed on the vehicle:
- Maintenance
- Repair
- Modification

They encode:
- What was done.
- Who did it (workshop or owner).
- When (date, odometer).
- Professional or DIY mode.

Node-signed execution events represent verified professional intervention.
Owner-reported execution events represent claimed DIY history.

When signed:
- They anchor lifecycle progression.
- They document intervention.
- They create accountable authorship.

Execution builds the structural backbone of the signal.

### 5.2 Inspection Events

Inspection events represent observed state at a specific point in time.

They encode:
- What was measured or evaluated.
- The condition observed.
- When (date, odometer).
- Who performed the inspection (always a node).

Inspection events do not require prior execution events.
They stand independently as point-in-time validations.

But when they follow execution events — particularly DIY claims — they perform a critical function:

> An inspection event following an owner-reported execution event elevates the credibility of the prior claim by confirming that the expected mechanical state is consistent with what was reported.

Inspection validates condition, not authorship.
This is what allows DIY history to be progressively reinforced.

Inspection serves three roles:

1. **State validation** — snapshot of condition.
2. **Gap reinforcement** — reduces ambiguity between execution events.
3. **DIY reinforcement** — strengthens owner-reported entries.

Inspection does not replace execution; it validates continuity.

### 5.3 The Reinforcement Mechanism

The interaction between execution and inspection events creates a reinforcement loop:

1. Owner reports a DIY event. → Low-weight signal.
2. Vehicle is subsequently inspected by a node. → Inspection finds expected state consistent with the reported work.
3. Coverage and credibility increase. → The prior claim is structurally corroborated.

The opposite is also true:
If an inspection reveals a condition inconsistent with reported history, the structural inconsistency is recorded. The signal reflects this.

---

## 6. What Strengthens the Signal

### 6.1 Consistent, Continuous Node-Signed Events

The most powerful signal builder is a long, uninterrupted sequence of node-signed execution and inspection events with no unexplained odometer gaps.

### 6.2 Multiple Independent Nodes

When a vehicle's history involves signing by multiple independent nodes across its lifecycle, the signal gains additional structural credibility. No single node controls the entire history.

### 6.3 Inspection Events as Periodic Validation

Even in the absence of execution activity, periodic inspection events strengthen the signal by confirming current state and odometer continuity.

### 6.4 DIY Reinforced by Inspection

Owner-reported events that are subsequently corroborated through inspection contribute to signal credibility at a medium weight. They demonstrate transparency and receive structural reinforcement.

### 6.5 Structural Consistency Over Time

A signal that is internally consistent — where event sequences, odometer readings, and observed conditions form a coherent mechanical narrative — is a stronger signal than one with unexplained discontinuities, even if total event volume is similar.

### 6.6 Explicit Separation of Layers

The signal strengthens when:
- Proposal and authoritative layers remain clearly separated.
- Execution mode (DIY vs professional) is explicit.
- Event authority is attributable and traceable to verified nodes.
- Signed ledger entries remain immutable.
- Corrections are additive and transparent.

The signal strengthens through density + integrity + continuity.

---

## 7. What Weakens the Signal

Signal integrity is not permanent.
It can be eroded by structural properties of the event timeline.

### 7.1 Kilometer Gaps

Unexplained lapses in mileage coverage — periods where no events exist and odometer continuity cannot be confirmed — reduce verification coverage.

### 7.2 Timeline Inconsistencies

Events with contradictory odometer readings, implausible chronological sequences, or conflicting condition states introduce structural inconsistency. These are flagged and reduce signal quality.

### 7.3 Owner-Only History (Authority Dilution)

A vehicle whose history consists entirely of owner-reported events, with no node-signed execution or inspection, carries low signal weight. The record may be accurate — but it is structurally unverified.

More broadly, overreliance on owner-reported events without reinforcement, low node participation density, and weak signing discipline all dilute authority.

### 7.4 Long Undocumented Periods

Even if all documented events are signed, extended periods without any documented history represent lifecycle gaps. The signal cannot claim coverage for time periods that were never recorded.

### 7.5 Corrections and Amendments

When a signed event requires correction, the system handles this additively — a new event is created referencing the original. Corrections are visible. Repeated corrections, or corrections that indicate prior errors in fundamental data, reduce interpretive confidence in the affected portion of history.

### 7.6 Interpretability Failure

If market participants misinterpret the signal (e.g., equating high coverage with perfect condition), credibility erodes.

The signal must remain interpretable as:

> "How much of this vehicle's lifecycle is verifiably structured?"

Not:

> "Is this car flawless?"

### 7.7 Manipulability

If signing can be gamed, altered, or backdated without traceability, the signal collapses.

Signal integrity is non-negotiable.

---

## 8. How the Signal Becomes Economically Relevant

The signal does not become economically relevant by declaration.
It becomes relevant when market participants begin to use it.

The adoption curve follows a staged logic:

### Stage 1: Interpretable and visible

The signal must first be understandable by non-technical users.
Verification Coverage must communicate something meaningful at a glance:
> *This vehicle has a well-documented, node-verified history / This vehicle has significant gaps in documented history.*

At this stage, the signal exists but is not yet required.

### Stage 2: Referenced in transactions

As structured histories accumulate, sellers begin referencing verification coverage in listings.
Buyers begin requesting it.
Negotiating parties use it as a reference point.

At this stage, the signal is economically active — it affects price and negotiation dynamics.

### Stage 3: Incorporated by institutions

Insurers, financiers, and resellers begin querying the signal programmatically.
Risk assessment models incorporate coverage data.
High-value transactions reference the Official Vehicle Report.

At this stage, the signal is institutionally embedded — it affects underwriting, financing, and bulk acquisition pricing.

### Stage 4: Expected by default

Vehicles without structured history carry a structural discount.
Verification coverage becomes a standard reference point — not a differentiator, but a baseline.

At this stage, the market has internalized the signal. Absence is penalized, not just presence rewarded.

---

## 9. Signal Interpretability Model

The signal must be interpretable without requiring technical knowledge of the underlying architecture.

### 9.1 Core Interpretive Dimensions

Three dimensions communicate signal quality:

**Depth**: How much of the vehicle's lifecycle is covered by verified events?

**Density**: How frequently were events documented relative to usage (mileage and time)?

**Integrity**: Is the event timeline structurally consistent? Are there anomalies or contradictions?

### 9.2 Signal Interpretability Principles

- The signal must be readable at multiple levels of sophistication.
  - A private buyer needs: *high / medium / low confidence in this vehicle's history.*
  - A professional buyer needs: *coverage %, event density, structural anomalies.*
  - An institutional actor needs: *structured data access, anomaly flags, event breakdown by type and node.*

- The signal must communicate what is *not* verified, not just what is.
  - Gaps must be visible, not hidden.
  - Absence of history is a meaningful data point — the signal does not suppress it.

- The signal must distinguish between *volume of events* and *quality of verification*.
  - Many owner-reported events are not equivalent to fewer node-signed events.
  - Volume and credibility are separate dimensions.

Interpretation must answer:

1. How much of the lifecycle is verified?
2. Who performed and signed key interventions?
3. Are there structural gaps?
4. Is the timeline coherent?

The signal is not a single scalar number.
It is a structured representation of lifecycle integrity summarized through coverage and event authority.

Its power lies in clarity, not complexity.

### 9.3 What the Signal Does Not Claim

The Trust Signal does not claim to represent the absolute mechanical condition of a vehicle at any point in time.

It represents:
- What has been documented.
- What has been independently signed.
- How consistent and continuous that documentation is.

It does not guarantee:
- That undocumented events did not occur.
- That a vehicle is free of defects.
- That reported work was performed to a specific quality standard.

Its value is not omniscience.
Its value is structured, verifiable, manipulation-resistant evidence of lifecycle stewardship.

---

## 10. Signal Integrity as a Non-Negotiable Constraint

Signal integrity cannot be compromised for adoption or growth purposes.

If the signal can be easily manipulated, it loses its value as a trust mechanism.

Structural safeguards that protect integrity:

- Signing authority belongs exclusively to verified nodes.
- Owners cannot modify signed ledger events.
- Corrections are additive and visible.
- Immutability of the signed ledger is enforced.
- Inspection events are always node-signed.
- Owners cannot sign authoritative ledger entries.

The signal's long-term economic value depends entirely on the market's confidence that it cannot be easily fabricated.

A weaker, more flexible signal that is easier to game has no long-term value.
A harder, stricter signal that takes longer to build is the durable asset.

Infrastructure serves the signal — not the other way around.

---

## 11. The Core Insight

The Trust Signal is not about proving perfection.

It is about:

- Structuring lifecycle truth.
- Anchoring it in accountable authority.
- Making continuity legible.
- Reducing uncertainty discount.
- Converting invisible stewardship into economic differentiation.

If the signal becomes socially recognized, the market shifts:

From narrative-based trust
To infrastructure-based trust anchored in service-layer verification.

---

## 12. Relationship to Other Documents

This document formalizes the conceptual core of the product.

It derives from, and must remain consistent with:
- **Context Pack (00)**: architectural principles and event model.
- **Vision & Thesis (01)**: market inefficiency framing and transformation narrative.

It feeds into:
- **Business Model & Monetization (04)**: how signal value is monetized through reports, API access, and institutional integration.
- **Infra MVP PRD (05)**: which signal properties must be expressed in the first build.

Strategic changes to the signal model must first be reflected in the Context Pack.

---

Version: 2.0
Scope: Internal Founder Document
Dependencies: context-pack.md, document-architecture.md, vision-and-thesis.md
