# Verifier-First MVP — Decisions
## Vehicle Identity & Secondary Market Trust Layer

*Internal Founder Document — Not for distribution*
*Living document — Updated as challenges are resolved*
*Context: [context.md](context.md)*

---

## How to Read This Document

Each challenge from the [Verifier-First Pivot context document](context.md) is resolved here with a clear position, what gets built in the MVP, what is deferred, and what must be validated before building.

---

## Challenge 1 — Inspector Day-1 Incentive

**Decision: Fusion of Solutions A + B — Superior tool with white-label output.**

The inspector adopts the platform because it produces a better report than what they make today (Solution A), and that report feels like theirs (Solution B). These are not competing approaches — they are complementary layers of the same value proposition.

### What Gets Built

**Report generator as a superior tool:**
- Structured inspection form with customizable sections, fields, and checklists per vehicle system.
- Photo upload integrated into each section.
- Odometer, date, and vehicle identification (VIN/plate) as standard fields.
- Auto-generated professional report from the form data — visually superior to a Word/PDF template.
- Permanent, verifiable link for each signed report.

**White-label identity:**
- Inspector's brand prominent in the report: business name, logo, contact information.
- The platform appears as verification infrastructure, not as the face of the report — a footer-level attribution ("Verificable en [plataforma]").
- The inspector's reaction to the output should be "this is *my* report, but better" — not "this is someone else's platform where I appear."

**Customizable inspection structure:**
- The inspector defines their own template: sections, order, items within each section.
- Different inspectors organize their methodology differently (e.g., electrical as a standalone section vs. distributed across engine/interior/etc.). The tool adapts to the inspector, not the reverse.
- Templates are reusable across inspections — define once, use on every job.
- Each item supports free-text observations + optional normalized tags (vehicle system, finding type, severity).

### What Is Deferred

- Full visual customization (colors, fonts, custom layouts) — MVP uses a professional fixed design with the inspector's branding inserted in predefined positions.
- Multiple templates per inspector (e.g., one for pre-purchase, another for periodic) — MVP starts with one template per inspector.
- Mandatory normalized tags on findings — in MVP, tags are optional to avoid adding friction to adoption.
- Inspector reputation metrics, badges, and tiers (addressed in Challenges 4 and 7).
- Public inspector profile beyond basic identity (name, contact, inspection count).

### What Must Be Validated Before Building

Through inspector conversations (3-5 inspectors):
- How do they produce their report today? What tool/template do they use?
- How long does it take to produce a report?
- Show a mockup of the white-label report — do they perceive it as an upgrade or as a threat to their independence?
- How do they organize their inspection methodology? What sections, what order, what level of detail?
- What information do they include today vs. what they would include if the tool made it easy?

### Key Design Principle

The platform is invisible infrastructure. The inspector is the brand. If the tool is good enough, signing and platform accumulation happen as side effects of using a better report generator — not as the primary ask.

### Risk to Monitor

Optional normalized tags may not get used, which would leave the platform without structured data for cross-inspector metrics (Challenge 4) and rigor comparison (Challenge 7). This is the correct trade-off for day 1 — an inspector who uses the tool without tags is better than one who doesn't use the tool because of mandatory metadata. Tag adoption can be encouraged through UX design and revisited post-launch.

---

## Challenge 2 — Seller Willingness to Pay for Pre-Sale Inspection

**Decision: Do not force seller-pays. Maintain buyer-pays as the default. Open a third channel through agencies.**

This challenge does not change the MVP's build scope. The inspection flow is agnostic to who pays — the inspector receives a request, performs the inspection, generates the report. Who commissioned it is a data point on the report, not a product change.

### Position

Three demand channels, in order of expected activation:

1. **Buyer-pays** — The status quo. This is how the market works today. Day-1 default.
2. **Seller-pays** — Emerges organically as verified report links become recognized in listings. Not forced, not pitched as a feature. It happens when sellers realize a verified inspection link makes their listing more competitive.
3. **Agency-pays** — Used car agencies focused on customer service (e.g., agencies that offer a package of services to sellers) incorporate the verified inspection as part of their value proposition. The agency has its own incentive: differentiation from competing agencies, justification for their fee, and buyer trust in the vehicles they list.

### What Gets Built

- A field on the inspection indicating who requested it (buyer / seller / agency / other). This is displayed transparently on the report (connects to Challenge 3).
- No special flows, pricing, or features for any specific channel. The tool is the same regardless of who pays.

### What Is Deferred

- Active seller-pays go-to-market. The shift happens organically or not at all in Phase 1.
- Agency-specific features (bulk inspections, agency dashboards, portfolio views).
- Any pricing differentiation based on who commissions the inspection.

### What Must Be Validated Before Building

Through seller conversations (3-5 recent sellers):
- Did they consider doing a pre-sale inspection? Why or why not?
- If they could include a verified inspection link in their listing, would they? Would they pay for it?
- How much did they sell for? What is the inspection cost as a percentage?

Through agency conversations (1-2 agencies):
- Do they already offer any type of inspection as part of their service?
- How do they document it?
- Would a verified, shareable report be valuable as part of their package?

### Key Insight

The agency channel is valuable because it sidesteps the individual seller behavioral change problem entirely. The agency already has a services model — the verified inspection is an additional line item in their package, not a new behavior for a private seller who has never paid for this before.

---

## Challenge 3 — Buyer Trust in Seller-Commissioned Inspections

**Decision: Transparency about who commissioned + second-opinion by design. No platform-level quantification of negative findings.**

### Position

Three mechanisms, each at a different level:

**A) Explicit transparency about who commissioned — Built in MVP.**
The report clearly states who requested the inspection (buyer / seller / agency). This is not hidden or minimized — it is surfaced prominently. The buyer decides based on the inspector's report content and identity, not on who paid.

**B) Negative findings as organic credibility — Not quantified by the platform in Phase 1.**
A report that says "brake wear at 60%, repainted rear door, otherwise normal condition" is inherently more credible than one that says "everything perfect." This credibility signal works organically when a buyer reads the report — it does not need the platform to measure or display it. In Phase 1, the platform does not surface finding rate as an aggregated metric due to risk of inflated findings. Finding rate is reintroduced as a visible metric in Phase 2 alongside tiers and other reputation signals, once volume exists to detect and counterbalance gaming (see Challenge 4 and 7).

**C) Second-opinion inspections — Emergent, no special build required.**
If a buyer does not trust the seller's inspection, they commission their own from a different inspector. Both inspections appear on the same vehicle page. Two independent inspections that substantially agree create high confidence. The *possibility* of cross-verification disciplines inspector behavior even when it is not exercised. This requires no special feature — it is a natural consequence of the vehicle page showing all inspections chronologically.

### What Gets Built

- "Requested by" field displayed prominently on every report (buyer / seller / agency / other).
- Vehicle page listing all inspections for the same VIN — enabling organic second-opinion visibility.

### What Is Deferred

- Any aggregated finding metrics on the inspector profile (finding rate, negative finding percentage).
- Structured comparison view between multiple inspections of the same vehicle.
- Automated cross-validation or agreement scoring between inspectors.

### Key Design Principle

Credibility signals must emerge from report content, not from platform-computed metrics. The platform provides transparency and structure. The buyer interprets.

---

## Challenge 4 — Reputation Measures Quantity, Not Quality

**Decision: Implicit rigor metrics (Solution A) + post-purchase reviews (Solution B) in MVP. Finding rate, tiers, and cross-validation introduced in Phase 2 with volume.**

### Position

The reputation system is built in two stages:

**Phase 1 (MVP):** Safe metrics that measure effort and thoroughness, plus post-purchase reviews. These are sufficient for a small, curated inspector base where the platform knows each inspector personally.

**Phase 2 (with volume):** Finding rate, average observations per report, tiers, and eventually cross-validation. These metrics become meaningful — and the inflation risk becomes manageable — once there is enough data to detect anomalies and enough reviews to counterbalance gaming.

The full vision is a combination of stats (inspection count, finding rate, avg observations, detail level), tiers (based on sustained activity and metric thresholds), and reviews — giving serious inspectors empirical proof that they are better than unqualified competitors. But this vision requires volume to be credible. Showing a finding rate based on 8 inspections is noise, not signal.

### What Gets Built (Phase 1)

**Safe implicit metrics (displayed on inspector profile):**
- **Inspection count** — total signed inspections.
- **Average detail level** — sections completed, photos attached, observations written per report.
- **Operating since** — date of first signed inspection.

**Post-purchase reviews:**
- After a transaction, the buyer who used a verified inspection report can leave a structured review: "Did the vehicle's condition match the inspection report?" (Yes / Partially / No) + optional free-text comment.
- Reviews are displayed on the inspector's profile and on the specific inspection report.
- Review volume will be low initially — this is expected. Even a few reviews carry meaningful signal.

### What Is Built in Phase 2 (With Volume)

- **Finding rate** — percentage of inspections where at least one issue was reported. Deferred from Phase 1 due to inflation risk with small numbers, but valuable as a differentiation metric once volume makes anomalies detectable.
- **Average observations per report** — more granular than detail level; measures depth of analysis.
- **Tier badges** — objective tiers based on metric thresholds (e.g., "200+ inspections, 90%+ finding consistency"). See Challenge 7.
- **Cross-validation between inspectors (Solution C)** — statistical comparison when multiple inspectors inspect the same vehicle. Requires multi-inspection vehicles to be common.

### What Must Be Validated Before Building

- Through buyer conversations: would they leave a review after purchase? What would make them more or less likely to do so?
- Post-launch: monitor review submission rate. If below 5% of inspections that lead to purchases, consider incentive mechanisms (but avoid making reviews transactional).

### Risk to Monitor

Review volume may be too low to be meaningful for months. This is acceptable — the implicit metrics (inspection count, detail level, operating time) provide a baseline signal while reviews accumulate. The inflation risk for finding rate is managed by deferring it to Phase 2 when volume and reviews provide counterbalancing signals.

---

## Challenge 5 — Phase 1 Monetization

**Decision: Revenue = 0 in Phase 1. Optimize for traction metrics that make the project fundeable.**

### Position

The three original candidate solutions (inspector SaaS subscription, commission on verified report upsell, freemium by volume) all create friction for the supply side. Every barrier to inspector adoption — no matter how small — works against the primary objective: maximizing signed events.

The platform's own monetization principle (see [Business Model & Monetization](../../business-model-and-monetization.md)) states it clearly: "Free whenever the user action increases signal supply." Inspectors are pure supply side. Charging them in Phase 1 is charging the people who build the asset.

Revenue in Phase 1 is not the goal. The goal is producing the traction evidence needed to raise funding.

### Phase 1 — What Matters

**Primary metrics (the funding story):**
- Active inspectors (using the tool recurrently without prompting).
- Signed inspections per month (event volume).
- Verified links appearing in marketplace listings (organic distribution).
- Buyer engagement with verified links (open rate, time on page).
- Inspector retention (% still active after 30/60/90 days).

These metrics demonstrate that the flywheel is turning. Revenue follows from a position of strength, not desperation.

### Phase 2 — Where Revenue Comes From

Revenue is not designed in Phase 1 — it is enabled by Phase 1 traction. Possible monetization paths once the platform has recognition:

- SaaS subscription for inspectors who already depend on the tool (switching cost is real by then).
- Premium artefacts for transactions (downloadable reports, formal documentation).
- Agency channel (setup, volume agreements).
- Marketplace or lead generation layer.

The specific path depends on what Phase 1 data reveals about where value concentrates. Committing to a monetization model before that data exists is premature.

### What Gets Built

- Nothing monetization-related. No paywalls, no subscription flows, no billing.
- Analytics and tracking infrastructure to measure the traction metrics listed above — this IS the Phase 1 deliverable for the business side.

### What Is Deferred

- All billing and subscription infrastructure.
- Pricing model selection.
- Revenue forecasting.

### Key Insight

The runway constraint is real but the answer is funding, not premature monetization. Premature monetization slows adoption, which weakens the funding story, which makes the runway problem worse. The virtuous path is: free tool → fast adoption → strong metrics → fundeable.

---

## Challenge 6 — An Inspector Can Replicate This Independently

**Decision: Solutions A and B are the same answer at different timescales. The tool captures; the network retains.**

### Position

An individual inspector can replicate any single capability: a website, a Google Doc template, an Instagram portfolio. This is true and will remain true. The platform does not compete on any individual feature.

The answer operates at two levels that are really one continuous argument:

**Day 1 — The artefact is better (Solution B).** A verified inspection link with a professional OpenGraph preview (vehicle photo, inspection summary, inspector identity, verification status) that renders correctly when pasted into MercadoLibre or Facebook Marketplace is a fundamentally better sharing artefact than a Google Doc link or a PDF attached to a WhatsApp message. No individual inspector will invest in building this. The platform provides it as shared infrastructure — for free.

**Day 180 — The network is unreplicable (Solution A).** The inspector's work appears on a vehicle page alongside inspections from other inspectors. Buyers search by VIN and find everything known about a vehicle in one place. The inspector's profile has accumulated history and reviews that cannot be ported to a personal website. Cross-inspector vehicle history, VIN-based search, and accumulated reputation are network properties that only a multi-inspector platform can offer.

These are not two separate solutions. They are the same value proposition at different stages of maturity. The tool captures the inspector on day 1. The network makes it irrational to leave on day 180.

### What Gets Built

- Optimized OpenGraph preview for verified report links — professional rendering when shared in marketplace listings and messaging apps.
- Vehicle page (by VIN) aggregating all inspections from all inspectors.
- Inspector profile page with accumulated inspection history.

### What Is Deferred

- VIN search as a consumer-facing feature (the vehicle page exists but is not actively marketed to buyers in Phase 1).
- Inspector discovery or directory features.

### Key Design Principle

Do not try to lock inspectors in through restrictions. Lock them in through accumulated value they cannot take with them. The platform wins by being genuinely more useful, not by creating switching costs through artificial barriers.

---

## Challenge 7 — Serious Inspectors May Reject Sharing a Platform with Unqualified Competitors

**Decision: Gatekeeping at entry + visible differentiation through metrics and tiers. Both solutions from the context document apply, but at different layers.**

### Position

The concern that serious inspectors reject sharing a platform with unqualified competitors is resolved at two levels:

**Layer 1 — Gatekeeping: not everyone can be a signing node.**

This is a structural requirement inherited from the original architecture. Inspectors on the platform are verified signing nodes — their signature carries weight because the platform has verified them as legitimate actors. This is not an open, P2P platform where anyone creates an account and starts verifying vehicles.

In Phase 1, inspectors are acquired through direct hunting. The founder identifies, contacts, and onboards each inspector personally. There is no application flow to approve or reject — the inspector is on the platform because they were specifically sought out. This is the reality of early-stage supply-side acquisition.

In Phase 2, as the platform gains recognition, an application and verification flow becomes necessary. At that point, the platform defines minimum requirements for node verification (established business, verifiable identity, relevant experience or equipment). The bar is not arbitrarily high — it exists to ensure that a signed inspection carries baseline credibility.

**Layer 2 — Visible differentiation: make the difference empirical, not gatekept.**

Once an inspector is verified and on the platform, the differentiation between a serious inspector and a less rigorous one is made visible through metrics, not through access restrictions. This is Solution A from the context document: if the serious inspector has 300 inspections, high detail level, and strong reviews, and the less rigorous one has 15 inspections with minimal detail — the platform is doing the differentiation work that the market cannot do today.

The serious inspector should want less rigorous inspectors on the platform because the comparison favors them empirically. The platform provides the data; the market interprets it.

**Layer 3 — Tiers as Phase 2 formalization.**

Objective tier badges (Solution B) formalize the differentiation once volume makes the metrics meaningful. Tiers are mathematical, not subjective: based on inspection count, detail level consistency, review scores, and finding rate (reintroduced in Phase 2 per Challenge 4). The less rigorous inspector can enter. Reaching the same tier requires sustained, real activity.

### What Gets Built (Phase 1)

- **Manual inspector onboarding** — no self-signup for verifier accounts. Each inspector is hunted and onboarded directly.
- **Inspector profile with basic metrics** — inspection count, detail level, operating since (per Challenge 4).
- **Post-purchase reviews** on inspector profile (per Challenge 4).
- The data infrastructure to support future tiers (metrics are tracked from day 1 even if tiers are not displayed yet).

### What Gets Built (Phase 2)

- **Application and verification flow** — for inspectors who want to join. Includes minimum requirements and platform review.
- **Tier badges** — objective, metric-based tiers displayed on inspector profiles and reports.
- **Full metrics suite** — finding rate, average observations, detail consistency (per Challenge 4 Phase 2).

### What Must Be Validated Before Building

Through inspector conversations (same conversations as Challenge 1):
- How do they feel about sharing a platform with less qualified competitors?
- Would visible metrics and tiers address their concern, or do they want harder gatekeeping?
- What would they consider minimum requirements for someone to be a verifier on the platform?

### Key Design Principle

Gatekeeping protects signal integrity (not everyone can sign). Visible differentiation protects inspector incentives (the serious ones can prove they are better). These are complementary, not alternatives. The platform gates entry to protect the signature's meaning, and then lets metrics and market interpretation handle the rest.

---

## Challenge 8 — Pre-Purchase Inspection Volume May Be Too Low

**Decision: Expand the definition of inspection beyond pre-purchase (Solution A). Geographic concentration (Solution B) is an operational decision, not a product decision.**

### Position

Pre-purchase inspections are the entry point, not the ceiling. The same tool and flow support multiple inspection types without product changes — the customizable template (Challenge 1) already handles this. The only addition is a "type of inspection" field to categorize events.

**Inspection types by priority:**

1. **Pre-purchase inspections** — the original case, day 1. This is where the verified link has immediate, obvious value.
2. **Workshop intake inspections** — documenting vehicle state upon arrival at a workshop. High volume potential (every vehicle entering a workshop is an opportunity). This is also the bridge to workshops (Challenge 9).
3. **Insurance condition documentation** — possible but depends on institutional relationships that do not exist in Phase 1. Deferred.
4. **Periodic voluntary inspections** — negligible volume today. Not worth designing for specifically.

A critical observation that reduces the urgency of this challenge: **many pre-purchase inspections are already performed at workshops.** Inspectors are often mechanics or workshops themselves. The boundary between "inspector" and "workshop" is blurry in practice — they are frequently the same actor wearing different hats. This means the platform naturally has a foot in both worlds from day 1, even before explicitly targeting workshops.

### What Gets Built

- An "inspection type" field on the inspection form (pre-purchase / intake / periodic / other). Categorizes the event without changing the flow.
- No type-specific features or flows. The tool is the same regardless of inspection type.

### What Is Deferred

- Insurance-specific documentation flows or integrations.
- Type-specific report templates (e.g., a lighter template for intake vs. a comprehensive one for pre-purchase). In MVP, the inspector's single customizable template handles all types.
- Market sizing analysis for the target geography (needed but does not block the build).

### Key Insight

The volume concern is mitigated by three factors working together: (1) expanding inspection types beyond pre-purchase, (2) the natural overlap between inspectors and workshops, and (3) intake inspections as a high-frequency use case once workshops are onboarded. Pre-purchase alone may be insufficient volume. Pre-purchase + intake + the inspector-workshop overlap changes the math significantly.

---

## Challenge 9 — The Transition from Inspectors to Workshops Is Not Automatic

**Decision: The intake inspection is the bridge (Solution B). Do not force the transition — let it emerge from the natural overlap between inspectors and workshops, plus owner pull (Solution A).**

### Position

The transition from inspectors to workshops is not a single leap — it is a gradient with multiple natural stepping stones:

**Step 1 — Many inspectors ARE workshops.**
The context document treats inspectors and workshops as separate actor types. In practice, many pre-purchase inspectors are mechanics who also run workshops, or workshops that offer inspection services. These actors are already on the platform as inspectors. The "transition" for them is not adopting a new tool — it is using the same tool for a different purpose (documenting work performed, not just vehicle state observed).

**Step 2 — Workshop intake inspection as a bridge.**
For workshops that are not already on the platform as inspectors, the intake inspection is the entry point. The pitch is not "register your work on our platform" — it is "document the vehicle's state before you work on it, so you have evidence if the client disputes later." This is pure self-protection for the workshop. It uses the same inspection tool already built and validated with inspectors. The workshop becomes an inspection-tool user first, not a CRM user.

**Step 3 — From intake documentation to signed work events.**
Once a workshop is using the inspection tool for intake documentation, the distance to also registering completed work as signed events shortens considerably. The tool is already in their workflow. The account exists. The vehicle is already in the system. Adding "what we did" after "what state it arrived in" is a natural extension, not a new adoption.

**Step 4 — Owner pull (emergent, not forced).**
When a vehicle has 2-3 verified inspections and arrives at a workshop, the owner may ask: "my vehicle has a verified history — can you add your work?" This is demand-side pull, not supply-side push. It depends on owners engaging with vehicle history (which depends on the flywheel working), so it is not relied upon — but it accelerates the transition when it happens.

### What Gets Built (Phase 1)

- Nothing specific for workshops. The inspection tool built for verifiers IS the workshop intake tool. No separate product, no separate flow.
- The "inspection type" field (from Challenge 8) accommodates intake inspections naturally.

### What Gets Built (Phase 2 — When Inspector Traction Is Demonstrated)

- **Execution events** — a second event type beyond inspections. Allows workshops to register work performed (not just state observed). This is the original "execution event" concept from the workshop-first MVP design, reintroduced when there is a workshop base ready to use it.
- **Workshop-specific onboarding** — a distinct pitch and entry flow for workshops that are not inspectors. Focused on intake protection, not CRM replacement.

### What Must Be Validated

- Through inspector conversations: do any of the early inspectors also run workshops? Would they use the same tool for intake documentation?
- Through workshop conversations (Phase 2, when inspector traction exists): does the intake protection pitch resonate? Would they document vehicle state on arrival if the tool were easy enough?
- Observation: do owners of vehicles with verified inspection history ask their workshops to add work to the history?

### Key Design Principle

The workshop transition is not a product pivot — it is a scope expansion of the same tool. Inspectors document observed state. Workshops document observed state (intake) and then work performed (execution). The underlying infrastructure is the same. The transition is gradual, not binary.

---

## Challenge 10 — Distance Between "Verified Inspections" and "Vehicle Identity Infrastructure"

**Decision: The vision is infrastructure. Inspections are the entry point, not the destination. The architecture is designed for infrastructure from day 1.**

### Position

The framing is not "we are building a verified inspection platform that might become infrastructure." The framing is: **"We are building vehicle identity infrastructure that resolves information asymmetry in the secondary market. Verified inspections are the first event type the system captures, because inspectors are the actor with the lowest adoption friction."**

This is not a rhetorical distinction. It has architectural consequences:

- The VIN is the central entity, not the inspector or the inspection.
- Events are the atomic unit — inspections are one type of event, execution events (workshop work) are another.
- Signing nodes are the trust authority — inspectors are one type of node, workshops are another.
- The vehicle page accumulates all events from all node types over the vehicle's lifecycle.

The system is designed as infrastructure from day 1. The go-to-market starts with inspectors because they are the lowest-friction signing node. But the data model, the event architecture, and the vehicle-centric identity are all built for the broader vision.

### The Honest Assessment of Distance

The distance between "inspectors signing pre-purchase inspections" and "insurers buying lifecycle data via API" is real and large. The path requires:

1. Inspectors adopt and produce signed inspection events → **Phase 1 (current)**
2. Workshops join through intake inspections and the inspector-workshop overlap (Challenge 9) → **Phase 2**
3. Execution events enrich vehicle histories beyond point-in-time inspections → **Phase 2**
4. Vehicle pages become meaningful lifecycle records → **Phase 2-3**
5. Density reaches a threshold where institutional actors can model the data → **Phase 3**

Each step has a verifiable threshold. The critical transition is step 2 — workshops joining. Without workshops, vehicle histories remain collections of inspection snapshots. With workshops, they become longitudinal lifecycle records. This is what makes Challenge 9 existential, not optional.

### What This Means for the MVP

The MVP is built as infrastructure that happens to serve inspectors first:

- Vehicle as central entity (by VIN), not inspector-centric.
- Event model that supports multiple event types (inspection now, execution later).
- Node model that supports multiple node types (inspector now, workshop later).
- Vehicle page that aggregates all events from all sources chronologically.

Nothing in the MVP is designed exclusively for inspections in a way that would need to be rebuilt for workshops. The architecture serves the long-term vision. The go-to-market serves the short-term reality.

### The Kill Condition

If the bridge to workshops (Challenge 9) fails — if workshops do not join through intake inspections, the inspector-workshop overlap does not materialize, and owner pull does not emerge — then the vision of vehicle identity infrastructure is not achievable through this path. The inspection business alone is not a viable standalone business: the market is too small and there is no sustainable monetization path for a platform that only captures point-in-time inspection events from a small pool of inspectors.

This is not a reason to avoid starting with inspectors. It is a reason to monitor the workshop bridge signals aggressively and to design every Phase 1 decision with the workshop transition in mind.

### What Must Be Validated

This challenge is validated indirectly through the other challenges:
- Challenge 9 validation (workshop bridge) is the primary gate.
- Challenge 8 validation (volume beyond pre-purchase) provides early signal.
- The inspector conversations (Challenge 1) should probe whether early inspectors also operate as workshops — this is the earliest indicator of whether the overlap hypothesis holds.

### Key Design Principle

Build infrastructure. Deploy it to inspectors first. Every architectural decision must serve the long-term vision, even when the short-term user is an inspector producing pre-purchase reports. The go-to-market is tactical. The architecture is strategic.

---

*All 10 challenges resolved.*
