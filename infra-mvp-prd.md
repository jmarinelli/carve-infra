# 05 — Infra MVP PRD
## Vehicle Identity & Secondary Market Trust Layer

*Internal Founder Document — Not for distribution*
*Version: 2.0*
*Derived from: context-pack.md v0.3 | document-architecture.md v0.2 | incentive-and-adoption-model.md v2.0 | signal-and-trust-model.md v2.0*
*Consolidated from: infra-mvp-prd-claude.md v1.0 | infra-mvp-prd-gpt.md v1.0*

---

## 1. Purpose and Scope

This document defines the first build: the minimal infrastructure required to instantiate the trust signal, support the node signing model, and begin accumulating verified ledger events.

This PRD covers:

- Core entities and their relationships.
- Event proposal vs. ledger event model.
- Signing flow.
- Inspection event model.
- Vehicle claim flow.
- Permission model.
- Basic Verification Coverage logic.
- Workshop operational panel (minimum viable).

This PRD does not cover:

- Marketplace or listing features.
- Advanced analytics or reporting dashboards.
- Deep monetization logic or billing systems.
- Institutional API layer.
- Official Vehicle Report generation.
- Risk scoring engine.

The MVP exists to validate the infrastructure core: can verified ledger events be created, signed, and accumulated? Can the system produce a meaningful, honest Verification Coverage signal from day one?

Everything else is post-MVP.

---

## 2. Core Entities

### 2.1 Vehicle

The primary entity. All events, coverage signals, and identity data attach to the vehicle.

**Attributes:**
- `id` — internal system identifier.
- `vin` — Vehicle Identification Number (primary external identifier).
- `make`, `model`, `year` — decoded or manually entered.
- `plate` — optional; jurisdiction-specific.
- `status` — `unclaimed` | `claimed`.
- `owner_id` — nullable; populated on claim.
- `created_by` — `owner` | `node`; records who initiated the vehicle entry.
- `created_at` — timestamp.

**Constraints:**
- VIN is unique in the system.
- A vehicle may exist without an owner (unclaimed).
- Nodes may create vehicles. Owners may create vehicles.
- VIN-based creation is the canonical flow; non-VIN entry is an exception.
- Vehicle history persists across ownership changes. The ledger belongs to the VIN, not the owner.

---

### 2.2 User

A single account representing a human in the system. Users authenticate once and may hold one or both roles.

**Attributes:**
- `id`
- `email`
- `phone` — optional.
- `display_name`
- `role_flags` — `owner` | `node_member` | both.
- `node_id` — nullable; populated if the user belongs to a node.
- `created_at`

**Why a unified user model:** In practice, a workshop owner also owns personal vehicles. A mechanic may want to track their own car. Forcing separate accounts for the same person creates friction and authentication complexity. A single user entity with role flags is simpler to build, simpler to authenticate, and reflects reality.

**Role: Owner**

Capabilities:
- Claim a vehicle.
- Create event proposals for owned vehicles (execution, DIY only).
- View signed ledger events for owned vehicles.
- View Verification Coverage for owned vehicles.
- Access the public verification page for any vehicle.

Restrictions:
- Cannot sign ledger events.
- Cannot modify signed ledger entries.
- Cannot create or sign inspection events.

**Role: Node Member**

Capabilities (exercised on behalf of their associated node):
- Create vehicles by VIN.
- Create event proposals (for any vehicle they interact with).
- Sign execution events their node performed.
- Create and sign inspection events.
- View their node's signed event history.
- Access the workshop operational panel.

Restrictions:
- Cannot modify signed ledger events.
- Cannot claim vehicle ownership (in their node member capacity).
- Cannot sign events their node did not perform or inspect (enforced by policy; not purely technical in MVP).

---

### 2.3 Node

A verified entity authorized to sign ledger events. In the MVP, nodes are workshops.

**Attributes:**
- `id`
- `display_name`
- `type` — `workshop` (only type in MVP).
- `address` — physical location.
- `contact_email`
- `contact_phone`
- `status` — `active` | `suspended`.
- `verified_at` — timestamp of verification.
- `created_at`
- `authorized_users` — list of user IDs authorized to act on behalf of this node.

**Constraints:**
- A node may have one or more authorized users (node members).
- Signing authority belongs to the node entity; individual users execute signing actions on the node's behalf.
- Node identity — not individual user identity — is the signing authority recorded on ledger events.

**Node verification:** Node onboarding is handled manually or via a lightweight verification flow in MVP. The system does not automate node verification at this stage.

---

### 2.4 Event Proposal

A structured, editable record of a service or inspection event. Proposals are not authoritative. They represent claimed or planned events awaiting signing — or, in the case of owner-reported events, they may remain permanently unvalidated.

**Attributes:**
- `id`
- `vehicle_id`
- `proposed_by_user_id` — the user who created the proposal.
- `proposed_by_role` — `owner` | `node_member`.
- `proposed_by_node_id` — nullable; populated if created by a node member.
- `event_type` — `execution` | `inspection`.
- `execution_mode` — `diy` | `professional` (required if `event_type = execution`).
- `title` — short descriptor (e.g., "Oil and filter change").
- `description` — free text; details of work performed or observed.
- `odometer_km` — reported odometer at time of event.
- `event_date` — reported date of event.
- `status` — `draft` | `pending_signature` | `signed` | `rejected`.
- `created_at`
- `updated_at`

**Lifecycle:**
- Created as `draft` by owner or node member.
- Node member submits as `pending_signature` when ready to sign.
- On signing, a Ledger Event is created and the proposal status transitions to `signed`.
- Owner-created proposals may remain in `draft` or `pending_signature` indefinitely if no node signs them.

**Editability:**
- Proposals are editable until signed.
- Once a Ledger Event is created from a proposal, the proposal is locked.

---

### 2.5 Ledger Event

An immutable, node-signed record representing a verified event in the vehicle's history.

**Attributes:**
- `id`
- `vehicle_id`
- `proposal_id` — references the originating proposal.
- `event_type` — `execution` | `inspection`.
- `execution_mode` — `diy` | `professional` (if execution).
- `title`
- `description`
- `odometer_km` — signed odometer at time of event.
- `event_date` — signed date of event.
- `signed_by_node_id`
- `signed_by_user_id` — the specific user who executed the signing action.
- `signed_at` — timestamp of signing.
- `linked_event_id` — nullable; used when an inspection event references an execution event, or when a correction event references an original event.
- `is_correction` — boolean; true if this event is a correction of a prior ledger event.

**Constraints:**
- Cannot be edited or deleted after creation.
- Only nodes may create ledger events (via the signing flow).
- Corrections are new ledger events, not mutations of existing ones.
- `signed_at` is set by the system at the moment of signing; it cannot be set by the node.
- `signed_by_node_id` is the authoritative signing identity; `signed_by_user_id` is recorded for internal audit trail.

---

### 2.6 Vehicle Claim

Represents an owner's assertion of current ownership of a vehicle.

**Attributes:**
- `id`
- `vehicle_id`
- `owner_id` (user ID with owner role)
- `claim_status` — `pending` | `active` | `superseded`.
- `claimed_at`

**Constraints:**
- A vehicle may have at most one active claim at a time.
- A prior claim is superseded when a new claim is made.
- The system does not verify legal ownership in MVP. Claim represents self-reported current ownership.

---

## 3. Event Proposal vs. Ledger Event Model

The system enforces a strict two-layer architecture. This separation is the structural foundation of signal integrity.

```
PROPOSAL LAYER                   LEDGER LAYER

  Owner / Node Member               Node Only

  [Event Proposal]  ──sign──►  [Ledger Event]

  Editable                          Immutable
  Not authoritative                 Authoritative
  Carries no coverage weight        Carries coverage weight
```

### 3.1 Why Two Layers

The proposal layer allows structured collection of claimed events without contaminating the authoritative record. An owner can describe their DIY oil change. A workshop can draft a service record before formally committing it. These drafts have no ledger authority until a node signs them.

This prevents the signal from being inflated by unverified self-reporting while preserving the practical value of capturing event data at proposal stage.

### 3.2 Proposal Creation Rules

| Actor | Can Create Proposal | Type |
|---|---|---|
| Owner | Yes | Execution (DIY) |
| Node Member | Yes | Execution (DIY or Professional) |
| Node Member | Yes | Inspection |

Owners cannot create inspection proposals. Inspection is a node-only event type.

### 3.3 Transition to Ledger Event

A ledger event is created when a node member:

1. Reviews a proposal (their own or an owner-submitted one).
2. Confirms or amends the proposal content.
3. Executes the signing action.

The signing action:
- Locks the proposal (`status → signed`).
- Creates an immutable ledger event with `signed_by_node_id`, `signed_by_user_id`, and `signed_at` set by the system.

A node may only sign proposals for:
- Execution events the node performed.
- Inspection events the node conducted.

In MVP, this is enforced by policy and node accountability, not by technical cryptographic signing. The system records the signing node identity and timestamp. Cryptographic signature infrastructure is a post-MVP enhancement.

### 3.4 Owner Proposals Without Node Signature

Owner-created proposals that are never signed remain as proposals. They are:
- Visible to the vehicle owner in their view.
- Not reflected in Verification Coverage.
- Not included in the authoritative ledger.
- Not displayed on the public verification page as verified events.

The system may surface them as "owner-reported, unvalidated" in the vehicle detail view, clearly distinguished from signed events.

---

## 4. Signing Flow

### 4.1 Node-Initiated Signing (Standard Path)

1. Node member creates an event proposal for a vehicle (by VIN lookup or vehicle search).
2. Node member fills in event details: type, title, description, odometer, date.
3. Node member reviews the proposal summary.
4. Node member submits the signing action.
5. System validates:
   - Node `status = active`.
   - Proposal `status = draft` or `pending_signature`.
   - Required fields present: `event_type`, `title`, `odometer_km`, `event_date`.
6. System creates ledger event with `signed_by_node_id = [node]`, `signed_by_user_id = [current user]`, and `signed_at = now()`.
7. Proposal transitions to `status = signed`.
8. Vehicle's Verification Coverage is recalculated asynchronously.

### 4.2 Owner-Submitted Proposal → Node Signing (Reinforcement Path)

1. Owner creates a DIY execution proposal for their vehicle.
2. Owner marks proposal as `pending_signature` and associates it with a specific node (optional in MVP; may simply appear in the node's queue if vehicle has been seen by the node).
3. Node member sees the owner-submitted proposal in their panel.
4. Node member reviews, optionally amends, and signs.
5. Ledger event is created referencing the original proposal.
6. Node signing the owner proposal does not assert that the node performed the work; it asserts that the node has reviewed and attests to the proposal's reasonableness. This distinction must be made explicit in the UI prompt at signing time.

> **Note on MVP scope:** The routing of owner proposals to specific nodes is a UX complexity. In MVP, it is acceptable for nodes to sign only their own proposals. Owner proposal reinforcement flow can be deferred to v1.1.

### 4.3 Correction Flow

If a signed ledger event contains an error (e.g., wrong odometer reading):

1. Node member creates a new event proposal marked `is_correction = true`, referencing the original ledger event ID via `linked_event_id`.
2. Node member signs the correction event following the standard signing flow.
3. Both the original and the correction event appear in the vehicle's ledger history.
4. The correction event is displayed with a visible reference to the original.
5. Neither event is deleted or modified.

---

## 5. Inspection Event Model

Inspection events are a first-class event type with distinct behavior.

### 5.1 Definition

An inspection event represents a node's observation of the vehicle's state at a specific point in time and odometer reading. It is not a record of work performed; it is a record of observed condition.

### 5.2 Inspection-Specific Attributes

In addition to base ledger event attributes:

- `inspection_type` — free text or predefined list (e.g., `pre_purchase`, `suspension`, `alignment`, `general_condition`, `dyno_measurement`, `safety_check`).
- `observed_condition_summary` — structured or free text description of what was observed.
- `linked_event_id` — optional; references a prior execution event that this inspection follows up on.

### 5.3 Rules

- Inspection events are always node-signed. There are no owner-created inspection proposals.
- An inspection event may stand alone (independent assessment).
- An inspection event may reference a prior execution event via `linked_event_id`, creating an explicit linkage: "this inspection confirms conditions related to event X."
- Inspection events carry the same coverage weight as execution events in Verification Coverage calculation.

### 5.4 Signal Function

As defined in the Signal & Trust Model:

- A DIY execution event reinforced by a subsequent inspection event moves from "owner-reported" to "DIY + Inspection" on the credibility gradient.
- Inspection events provide independent, node-sourced observations of vehicle state.
- They are particularly valuable in validating claimed DIY work and confirming mechanical state at mileage intervals.

---

## 6. Vehicle Claim Flow

### 6.1 Claim Initiation

An owner claims a vehicle by:

1. Searching the system by VIN or plate.
2. If the vehicle does not exist: creating a new vehicle record (by VIN).
3. If the vehicle exists (created by a node or another owner record): submitting a claim request.

### 6.2 Claim Validation

MVP claim validation is lightweight:

- Owner provides VIN and self-asserts current ownership.
- No legal ownership verification is performed.
- The system may optionally send a confirmation prompt (e.g., email or in-app confirmation step).
- Claim is set to `active` upon confirmation.

If a vehicle already has an active claim, the new claim supersedes it. The prior owner is notified (if contact information is available). The system logs the ownership transition.

### 6.3 Post-Claim State

After a successful claim:

- Owner can view the vehicle's full ledger history (including history that accumulated before their claim).
- Owner can create event proposals.
- Owner sees the vehicle's current Verification Coverage.
- Owner has access to the public verification page link for their vehicle.

### 6.4 Unclaimed Vehicles

Vehicles created by nodes without an owner claim continue to accumulate ledger events. Their history is publicly accessible via the verification page. Verification Coverage is calculated regardless of claim status.

This is the passive ledger accumulation mechanism: a vehicle can have a meaningful, growing signal before any owner ever claims it.

---

## 7. Permission Model

### 7.1 Permission Matrix

| Action | Owner | Node Member | Unauthenticated |
|---|---|---|---|
| Create vehicle by VIN | Yes | Yes | No |
| Claim vehicle | Yes | No | No |
| Create execution proposal (DIY) | Yes (own vehicle) | Yes (any vehicle) | No |
| Create execution proposal (professional) | No | Yes | No |
| Create inspection proposal | No | Yes | No |
| Sign ledger event | No | Yes | No |
| View own ledger events | Yes | Yes (own node's signed events) | No |
| View public verification page | Yes | Yes | Yes |
| View Verification Coverage (public) | Yes | Yes | Yes |
| View workshop operational panel | No | Yes | No |
| Modify signed ledger event | No | No | No |
| Create correction event | No | Yes | No |

### 7.2 Node Signing Constraint

A node can only sign proposals where the node is the executing or inspecting party. In MVP, this is a policy constraint enforced through UI flow design (node members only see their own node's proposals in the signing queue) rather than cryptographic enforcement.

### 7.3 Vehicle Visibility

- Ledger events: publicly accessible via the vehicle's verification page (by VIN).
- Owner identity: not exposed on the public verification page. Vehicle history is VIN-anchored, not owner-anchored.
- Node identity: signing node name is visible on signed ledger events. This is intentional — it creates accountability and supports the professional differentiation use case for workshops.

---

## 8. Basic Verification Coverage Logic

### 8.1 Design Principles

Coverage reflects the structural quality of a vehicle's signed history. It is not a vanity score. It is not gameable by volume alone.

In MVP, the coverage calculation is intentionally simplified. The goal is a credible, honest signal — not a sophisticated algorithm. The logic can be refined post-MVP as real data patterns emerge.

### 8.2 Coverage Inputs

Verification Coverage is derived from signed ledger events only. Owner-reported proposals contribute zero coverage weight.

**Primary inputs:**

1. **Signed event count** — total number of node-signed ledger events (execution + inspection).
2. **Odometer span covered** — the mileage range between the earliest and latest signed events with valid odometer readings.
3. **Event density** — signed events per X km bracket (to detect long gaps within covered span).
4. **Credibility weights** — execution by professional node and inspection events carry full weight; inspection reinforcement of DIY events carries full weight at the inspection level.

### 8.3 MVP Coverage Model (Simplified)

The MVP implementation uses a tiered signal rather than a computed percentage, to avoid false precision before sufficient data patterns exist.

**Why tiers instead of percentages:** With sparse early data (a few events across a vehicle's life), a percentage like "23% coverage" implies a precision that doesn't exist. It invites questions with no good answers ("what does 23% mean with 3 events?"). Tiers communicate the maturity of a vehicle's record honestly: either it has no history, early records, partial records, documented history, or strong verified history. Each tier has clear, defensible criteria. Percentages can be introduced post-MVP once real data patterns reveal meaningful thresholds.

**Coverage Tiers:**

| Tier | Label | Criteria |
|---|---|---|
| 0 | No Verified History | Zero signed ledger events. |
| 1 | Early Record | 1–2 signed events. Minimal odometer span. |
| 2 | Partial History | 3–5 signed events, or limited odometer coverage relative to vehicle age. |
| 3 | Documented History | 6+ signed events with reasonable odometer continuity and no large unexplained gaps. |
| 4 | Strong Verified History | High event density, consistent odometer progression, at least one inspection event, no major structural inconsistencies. |

**Gap detection (MVP):**

A gap is flagged when the odometer difference between two consecutive signed events exceeds a defined threshold (e.g., > 30,000 km without an intermediate signed event). Flagged gaps are surfaced as visible indicators, not silently absorbed.

**Inconsistency detection (MVP):**

If a signed event's odometer reading is lower than a prior signed event's reading (non-monotonic odometer), the system flags a structural inconsistency. This flag is visible on the vehicle's coverage display and reduces the tier ceiling.

Date sequence validation: if a signed event's date is earlier than a prior signed event's date while the odometer is higher, or vice versa, the system flags a temporal inconsistency.

### 8.4 Coverage Display

The public verification page and owner dashboard surface:

- Current coverage tier (label only in MVP; no computed percentage).
- Count of signed events.
- Odometer range covered by signed events.
- Flagged gaps (if any).
- Flagged inconsistencies (if any).
- Breakdown: execution events vs. inspection events.
- Credibility gradient summary: professional / inspection / DIY+inspection / owner-reported only.

Coverage is honest. Gaps are shown, not hidden. The display does not optimize for appearing strong; it optimizes for being accurate.

### 8.5 Coverage Update Trigger

Coverage is recalculated asynchronously each time a new ledger event is created for the vehicle.

---

## 9. Public Verification Page

### 9.1 Access

Accessible by VIN at a public URL. No authentication required.

URL pattern: `/v/{vin}` or `/verify/{vin}`

### 9.2 Page Contents

- Vehicle summary: make, model, year, VIN (partially masked or full — TBD based on privacy policy).
- Current Verification Coverage tier.
- Coverage indicators: event count, odometer span, flags.
- Signed event timeline: list of ledger events in chronological order.
  - Per event: date, odometer, event type, title, signing node name.
  - No sensitive free-text descriptions exposed publicly in MVP (descriptions available to authenticated owner only).
- Owner identity: not displayed.
- "Powered by [System Name]" attribution.

Must clearly distinguish:
- Verified (signed) events.
- Owner-reported (unverified) events, if surfaced.

### 9.3 Purpose

This page is the traveling artifact. It is shared in transaction contexts, referenced in listings, and presented as proof of documented history. Its design must communicate trustworthiness at a glance.

---

## 10. Workshop Operational Panel

The workshop panel is the primary interface for nodes in the MVP. It is functional, not decorative.

### 10.1 Panel Scope

The workshop panel provides the minimum functionality required for a node to:

- Create vehicles.
- Create and manage event proposals.
- Sign ledger events.
- View their signed event history.

It is not a CRM. It is not an appointment scheduler. It is not a billing tool. It is a structured event signing interface.

### 10.2 Panel Sections

**A) Vehicle Lookup / Entry**
- Search by VIN or plate.
- If vehicle not found: create by VIN.
- Quick access to recent vehicles the node has interacted with.

**B) Event Proposal Creation**
- Select vehicle.
- Select event type: execution or inspection.
- If execution: select execution mode (DIY or professional).
- Fill in: title, description, odometer, date.
- Save as draft or proceed to signing.

**C) Signing Queue**
- List of proposals in `draft` or `pending_signature` status created by this node.
- Per proposal: vehicle VIN, event type, title, date, odometer.
- Sign action: review summary → confirm → sign.
- Signed events removed from queue; appear in history.

**D) Signed Event History**
- Chronological list of all ledger events signed by this node.
- Filterable by vehicle VIN, date range, event type.
- Per event: vehicle VIN, make/model/year, event type, title, date signed.
- Ability to view full event detail.
- Link to the vehicle's public verification page.

**E) Node Profile (read-only in MVP)**
- Node name, type, address, contact info.
- Verification status indicator.

### 10.3 Out of Scope for Workshop Panel (MVP)

- Client management / contact database.
- Appointment scheduling.
- Revenue or job tracking.
- Inventory management.
- Multi-user node account management UI (users are associated to nodes in backend; no self-service management in MVP).
- Analytics or reporting dashboards.

### 10.4 Performance Requirement

Time-to-first-signed-event for a new node onboarded to the system must be achievable in under 10 minutes. The panel flow must support this.

---

## 11. Entity Relationship Summary

```
Vehicle (VIN)
  ├── Vehicle Claim → User (owner role)
  ├── Event Proposal (1..n)
  │     ├── Created by User as Owner (execution, DIY only)
  │     └── Created by User as Node Member (execution or inspection)
  └── Ledger Event (1..n) [immutable]
        ├── Signed by Node (via authorized User)
        ├── Linked to Proposal
        └── May link to prior Ledger Event (correction / inspection linkage)

User
  ├── May hold Owner role → Claims Vehicles, Creates DIY Proposals
  └── May hold Node Member role → Signs Events, Creates Proposals on behalf of Node

Node
  ├── Has authorized Users (node members)
  ├── Signs Ledger Events (via its members)
  └── Creates Event Proposals (via its members)
```

---

## 12. Out of Scope (Explicit Exclusions)

The following are explicitly excluded from this MVP:

- Marketplace or listing features.
- Lead generation for workshops.
- Buyer-seller transaction facilitation.
- Advanced analytics or aggregated data views.
- Official Vehicle Report generation (post-MVP).
- Institutional API access layer.
- Billing, subscriptions, or monetization flows.
- Multi-user node account management UI.
- Mobile-native application (web-responsive is sufficient for MVP).
- Cryptographic signing (policy-enforced signing is sufficient for MVP).
- Risk scoring or anomaly detection beyond basic flag logic.
- AI or automated data extraction features.
- Insurance integrations.
- Fleet management tools.

---

## 13. Success Criteria for MVP

### Primary Metric
- **Node-signed ledger events per month.** This is the atomic unit of value creation. If events are being signed, the system is working.

### Secondary Metrics
- **Average verification coverage tier per active vehicle.** Measures whether accumulated events are producing meaningful signal.
- **Workshop time-to-first-signature.** Measures onboarding friction. Target: under 10 minutes.

### Structural Invariants
These are not metrics — they are pass/fail constraints:
- No ability to alter signed ledger events (immutability holds).
- No signal integrity breaches (coverage derived exclusively from node-signed events).
- Gaps and inconsistencies are surfaced, never suppressed.

---

## 14. Key Constraints and Non-Negotiables

These constraints derive directly from the Signal & Trust Model and Context Pack. They are not open for negotiation in MVP or beyond.

1. **Only nodes sign ledger events.** Owners cannot sign anything.
2. **Signed ledger events are immutable.** No deletion. No editing.
3. **Corrections are additive.** New events reference old ones. Both remain visible.
4. **Owner-reported proposals carry no coverage weight.** Coverage derives exclusively from node-signed events.
5. **Gaps are visible.** The coverage display must surface gaps and inconsistencies, not suppress them.
6. **Node identity is visible on signed events.** Accountability is structural.
7. **Infrastructure serves signal.** Feature additions that compromise signal integrity are not built.

---

## 15. v1.1 Considerations

The following items surfaced during v2.0 consolidation as valuable but not MVP-critical. They are noted here for continuity:

- **Structured metadata on proposals** — execution subtypes (maintenance / repair / modification) as predefined categories rather than free text. Enables future analytics without complicating MVP data entry.
- **Attachments on proposals** — photos or documents attached to proposals before signing. Practically valuable for workshops documenting work visually.
- **Owner proposal routing to nodes** — the reinforcement path (Section 4.2) where owners submit DIY proposals for node review. Deferred due to UX complexity in routing.
- **Multi-to-one inspection linking** — allowing an inspection event to reference multiple prior execution events rather than a single `linked_event_id`. More flexible but adds implementation complexity.

These items are explicitly deferred, not rejected. They should be evaluated against real usage patterns from MVP data.

---

*Document 05 — Infra MVP PRD v2.0 | Internal Use Only*
*Dependencies: context-pack.md v0.3 | document-architecture.md v0.2 | incentive-and-adoption-model.md v2.0 | signal-and-trust-model.md v2.0*
*Consolidated from: infra-mvp-prd-claude.md v1.0 | infra-mvp-prd-gpt.md v1.0*
