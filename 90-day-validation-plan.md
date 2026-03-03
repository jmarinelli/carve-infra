# 06 — 90-Day Validation Plan
## Vehicle Identity & Secondary Market Trust Layer

*Internal Founder Document — Not for distribution*
*Version: 1.0*
*Derived from: context-pack.md v0.3 | document-architecture.md v0.2 | vision-and-thesis.md v2.0 | incentive-and-adoption-model.md v2.0 | signal-and-trust-model.md v2.0 | business-model-and-monetization.md v2.0*

---

## 1. Purpose of This Document

This plan exists to prevent idea drift.

The previous documents establish a coherent thesis, an adoption logic, a signal model, and a business model. None of that matters if the behavioral assumptions underlying them are wrong. This plan operationalizes the discipline of testing whether they are right — before committing significant resources to infrastructure built on unvalidated assumptions.

The 90-day window is not about building the product. It is about answering the hardest feasibility questions using the minimum viable evidence.

The standard for this period is not "does this feel promising?" It is: **"Is there structural evidence that the adoption model is viable, and that the signal can be produced consistently?"**

If the answer is no, this document defines the conditions under which the project must be killed or fundamentally restructured.

---

## 2. The Hypotheses

These are the foundational behavioral assumptions on which the entire architecture rests. Each one is a point of failure.

### H1 — Workshop Operational Value Is Real

**Statement:** Quality-oriented, digitally capable workshops will perceive immediate, tangible operational value from the node panel — independent of any market recognition of the trust signal.

**Why it matters:** Workshops are the supply side. If the operational value proposition is not real and compelling on its own, node-signed event growth flatlines from day one. Everything downstream depends on this.

**The honest concern:** Workshops may express interest but fail to integrate the signing workflow into their actual day-to-day operations. Interest ≠ behavioral change. This must be tested against real usage, not stated intent.

---

### H2 — Workshop Signing Behavior Persists After Initial Onboarding

**Statement:** Workshops that begin signing events will continue to do so habitually, not just at onboarding. The operational integration is durable, not episodic.

**Why it matters:** Early adoption is cheap to generate. Sustained behavior is what produces signal density. A workshop that signs 5 events and stops is not a node. It is a failed experiment.

**The honest concern:** Onboarding motivation and ongoing behavior are different phenomena. Many products show strong initial activity and rapid drop-off. This plan must be designed to detect that drop-off early.

---

### H3 — Owners Find Value When Encountering a Pre-Existing History

**Statement:** When vehicle owners discover that their vehicle already has a node-signed history — because workshops entered events prior to owner claim — they engage meaningfully with the platform rather than treating it as irrelevant.

**Why it matters:** Passive accumulation is the structural answer to owner inertia. If owners do not value pre-existing history upon discovery, the passive accumulation mechanism fails and owner activation becomes dependent on proactive evangelism — which does not scale.

**The honest concern:** Owners may look at the history, shrug, and leave. The system must demonstrate that discovery of prior history converts to claim behavior and ongoing engagement.

---

### H4 — The LATAM Informality Premium Hypothesis Is Directionally Correct

**Statement:** In the target market, a segment of buyers and sellers already perceives documented vehicle history as a meaningful differentiator — even if formalized verification infrastructure does not yet exist. There is latent demand for credible verification, not just stated preference.

**Why it matters:** If the market is genuinely indifferent to documentation — if transactions are entirely relational and informal with no appetite for structured proof — the consumer flywheel cannot spin. The trust signal would be valued only at the institutional level, which is a Phase 3 event years away.

**The honest concern:** In informal markets, the premium for documentation may be conceptually endorsed and practically ignored. Interviews and surveys will not detect this. Observed transaction behavior will.

---

### H5 — Workshop Onboarding Friction Is Conquerable in the Initial Target Profile

**Statement:** The specific workshop profile being targeted — quality-oriented, digitally capable, client-facing — can complete onboarding and reach their first signed event within one working session, without requiring dedicated technical support.

**Why it matters:** Time-to-first-signed-event is a direct friction proxy. If it requires multiple sessions, escalation, or significant support overhead, the model cannot scale even if the value proposition is correct.

**The honest concern:** "Digitally capable" workshops span a wide range. The product must be designed for the lower end of that range, not for tech-forward outliers.

---

## 3. Experiments

### Experiment 1 — Workshop Direct Outreach and Operational Pitch

**Objective:** Test whether workshops in the target profile respond positively to the operational value pitch and agree to participate as beta nodes.

**Method:**
- Direct outreach to 20–30 workshops in the initial geographic focus area.
- Profile filter: independent workshops with some digital infrastructure (invoicing software, WhatsApp for client communication, or equivalent), client-facing positioning, and services where documentation has visible value (major repairs, modifications, performance work, pre-purchase inspections).
- Pitch is operational only: structured job registry, client-facing service certificates, dispute protection. Do not lead with market signal or trust layer positioning.
- Measure: what proportion agree to proceed and complete onboarding?

**Expected learning:** Whether the operational pitch converts qualified workshops, and where the pitch fails or generates objections.

---

### Experiment 2 — Time-to-First-Signed-Event Test

**Objective:** Measure actual onboarding friction against the target threshold.

**Method:**
- For each workshop that agrees to participate, track time from onboarding initiation to completion of first signed ledger event.
- Observe where sessions stop, where questions arise, where the workflow breaks.
- Target threshold: first signed event completed within a single working session without escalation.

**Expected learning:** Concrete friction map. Specific workflow steps that exceed tolerance. Whether the target threshold is achievable with existing or prototype tooling.

---

### Experiment 3 — Signing Behavior Persistence Tracking

**Objective:** Determine whether initial workshop signing behavior is sustained over the 90-day window.

**Method:**
- Track signed event frequency per workshop across weeks 1–12.
- Segment workshops by profile characteristics and onboarding path.
- Flag any workshop that has signed events in week 1 but has zero signed events in weeks 5–8.
- Weekly check-in protocol for inactive workshops: a single structured conversation to understand why signing stopped.

**Expected learning:** Whether behavioral adoption is real or performative. Early warning signal for workshops that will churn.

---

### Experiment 4 — Passive Accumulation and Owner Discovery Test

**Objective:** Test whether owners who encounter pre-existing node-signed history engage with the platform at a meaningfully higher rate than owners approaching an empty vehicle identity.

**Method:**
- Identify vehicles serviced by beta workshops for which no owner claim exists.
- Create an owner-facing discovery flow: notification to the vehicle's known owner (via workshop contact or public-facing vehicle page) that their vehicle's history is available.
- Measure: claim rate, time-to-claim, post-claim engagement (any action taken within 7 days of claim).
- Control: track owner response to a minimal prompt (basic vehicle identity with no history) versus a history-populated vehicle.

**Expected learning:** Whether pre-existing history materially changes owner activation behavior.

---

### Experiment 5 — Observed Transaction Behavior Probe

**Objective:** Test whether verified history or the concept of structured service documentation influences transaction behavior in a real secondary market context.

**Method:**
- This is qualitative and structured, not quantitative at this stage.
- Identify 5–10 vehicle transactions in the target market (through seller or buyer contacts) across the 90-day window.
- In each case, conduct structured post-transaction interviews: Did history documentation come up? Did its presence or absence affect price or negotiation? What format of documentation carried credibility?
- Do not inject the product into transactions. Observe and probe what actually happened.

**Expected learning:** Whether there is organic demand for credible documentation in real transaction contexts — and what form of evidence buyers and sellers currently treat as meaningful.

---

### Experiment 6 — Dispute Protection Resonance Test

**Objective:** Determine whether the dispute protection value proposition is a strong independent motivator for workshop adoption, or whether it is a supporting argument.

**Method:**
- In outreach conversations with workshops, present the dispute protection argument in isolation — before mentioning any other feature.
- Prompt: describe a scenario in which a client disputed a service outcome. Ask how it was resolved. Ask whether a signed, timestamped record would have changed the situation.
- Record whether dispute history is present and whether the protection argument triggers visible recognition.

**Expected learning:** Whether dispute protection is a primary hook or a reinforcing argument. Determines whether it should lead the pitch or support it.

---

## 4. Metrics

### Primary Signal Metric

**Node-signed ledger events per month (from active beta workshops)**
This is the single most important operational metric. It captures whether the supply side is functionally working.

Target by end of month 3: a minimum of 3 workshops each signing at least 10 events per month consistently. Total signed events ≥ 100 across the period.

---

### Secondary Metrics

**Workshop conversion rate from outreach to first signed event**
Definition: proportion of workshops contacted that complete at least one signed event.
Target: ≥ 25% of qualified outreach.

**Time-to-first-signed-event**
Definition: elapsed time from beginning of onboarding to completion of first signed ledger event.
Target: ≤ 90 minutes within a single working session, without escalation.

**Workshop signing persistence rate**
Definition: proportion of workshops that signed events in weeks 1–4 who continue to sign events in weeks 5–12.
Target: ≥ 70% persistence rate across the cohort.

**Owner claim rate for history-populated vehicles**
Definition: proportion of identified vehicle owners who claim a vehicle after being notified of existing node-signed history.
Target: ≥ 30% claim rate within 14 days of notification.

**Qualitative signal from transaction probes**
Definition: proportion of observed transactions in which documentation or history was referenced by at least one party.
Target: ≥ 50% of probed transactions show some documentation reference — regardless of format.

---

### Red Flag Indicators (Immediate Attention Required)

- Any workshop that signed events in weeks 1–2 has zero events in weeks 5–6.
- Average time-to-first-signed-event exceeds 3 hours or requires multiple sessions.
- More than 50% of outreach conversations result in objections centered on tax visibility or data exposure.
- Zero owner claims generated from history-populated vehicle notifications in month 2.
- No transaction probe reveals any organic documentation discussion.

These are not kill criteria on their own. They are signals that a specific hypothesis is failing and that immediate diagnostic conversation is required.

---

## 5. Validation Thresholds

The following thresholds define what the 90-day evidence must demonstrate to justify proceeding to MVP build.

### Threshold 1 — Workshop Supply Side Is Functionally Viable

**Minimum condition:** At least 3 workshops are consistently signing events at the end of 90 days. Consistently means at least 8 events per month in months 2 and 3, without significant founder intervention required to maintain the behavior.

**What this confirms:** The operational value proposition is real and the adoption sequence is functionally sound at small scale.

---

### Threshold 2 — Onboarding Friction Is Within Manageable Range

**Minimum condition:** The median time-to-first-signed-event is under 90 minutes, achieved within a single session, for at least 5 workshops.

**What this confirms:** The onboarding path can be standardized and scaled without a high-touch support dependency.

---

### Threshold 3 — Signing Behavior Persists Without Active Maintenance

**Minimum condition:** At least 70% of workshops that signed events in weeks 1–4 continue signing in weeks 9–12 without requiring founder-initiated prompting.

**What this confirms:** The operational integration is real, not performative. The value is sufficient to sustain behavior beyond the novelty of onboarding.

---

### Threshold 4 — Owner Discovery Generates Nonzero Engagement

**Minimum condition:** At least 30% of owners notified of a pre-existing history claim their vehicle within 14 days. At least one claimed vehicle shows post-claim engagement (event proposal, sharing, or further interaction) within 7 days.

**What this confirms:** The passive accumulation mechanism creates a meaningful foundation for owner activation. The discovery moment converts.

---

### Threshold 5 — Latent Demand Signal Is Directionally Present

**Minimum condition:** In structured transaction probes, at least 3 of the 5–10 observed transactions include unprompted reference to documentation, history, or verifiability in any form. This does not need to reference the product — it must reveal that the problem exists behaviorally.

**What this confirms:** There is organic demand for the signal's underlying function, even if buyers and sellers do not yet have a structured way to access it.

---

## 6. Kill Criteria

These are conditions under which the project must be restructured or stopped. They are not reasons to pivot to a slightly different version of the same thesis. They are structural invalidations.

### Kill Criterion 1 — Workshop Signing Behavior Collapses

**Condition:** By the end of month 3, fewer than 2 workshops are actively signing events (defined as at least 5 events in the final 30-day period), AND outreach to additional workshops has not produced a qualified pipeline of candidates willing to onboard.

**What it means:** The supply side is not viable. Without consistent node-signed events, there is no signal. Without signal, there is no product. Operating value proposition is insufficient or workshop profile is wrong.

**Required response:** Full stop. Do not proceed to MVP build. Conduct structured post-mortems with all participating workshops. The question to answer: was the value proposition wrong, or was the target profile wrong? If profile, refine and retest. If value proposition, the fundamental adoption model requires revision before further investment.

---

### Kill Criterion 2 — Signing Persistence Falls Below Acceptable Threshold

**Condition:** Fewer than 50% of workshops that signed events in weeks 1–4 continue signing in weeks 9–12, despite founder intervention and active troubleshooting.

**What it means:** Initial adoption is not translating into durable behavior. The system is producing onboarding behavior, not operational integration. The product is not sufficiently embedded in the workshop's actual workflow.

**Required response:** Do not proceed to MVP build until a revised operational flow or deeper workflow integration is designed and tested with a new cohort.

---

### Kill Criterion 3 — Owner Discovery Generates No Meaningful Response

**Condition:** Owner claim rate from history-populated vehicle notifications is below 10%, and post-claim engagement is zero across the full 90-day window.

**What it means:** The passive accumulation mechanism does not activate owners. The discovery moment does not convert. If owners are indifferent to pre-existing verified history, the flywheel's consumer leg is broken. Owner adoption would require proactive evangelism at a cost and velocity that does not scale.

**Required response:** This does not kill the workshop-only model, but it kills the assumption that owner network effects will develop organically. Business model must be reassessed: can the product sustain itself as a B2B workshop tool without consumer-side traction? If yes, pivot the thesis accordingly. If no, stop.

---

### Kill Criterion 4 — Transaction Probes Reveal No Organic Demand for Documentation

**Condition:** Across 5–10 structured transaction probes, fewer than 2 transactions reveal any organic reference to documentation, history, or verifiability. Buyers and sellers operate in a purely relational, informal mode with no apparent appetite for structured evidence.

**What it means:** The LATAM informality premium hypothesis is wrong for the target segment and geography. The demand for the signal does not exist at the consumer level — at least not in the near term.

**Required response:** Reassess the consumer thesis. If institutional demand is structurally real but consumer demand is not, the adoption model must be rebuilt around workshop-to-institution pathways without relying on consumer-facing transaction signals. This requires a fundamental rewrite of the incentive model before further investment.

---

### Kill Criterion 5 — Tax Visibility Objection Is Systemic

**Condition:** More than 60% of outreach conversations with target-profile workshops raise tax visibility or fiscal exposure as a primary objection to participation — not an incidental concern, but a blocking concern.

**What it means:** The target market's informal economy dynamics are more constraining than anticipated. The workshop profile must be narrowed to formally compliant operations, which may represent too small a segment to build meaningful coverage from.

**Required response:** Before stopping, test whether narrowing to fully formal, compliant workshops (certified shops, dealer service centers, established inspection centers) generates a viable cohort. If that narrower profile can produce the same signal density, the model survives with a revised target profile. If it cannot produce density, the adoption model is fundamentally broken in the target geography.

---

## 7. Iteration Cycles

The 90-day window is structured into three 30-day cycles, each with a defined focus and decision gate.

---

### Cycle 1 — Days 1–30: Outreach, Onboarding, and First Evidence

**Objective:** Produce the first node-signed ledger events in a live environment. Establish initial workshop cohort.

**Activities:**
- Complete outreach to 20–30 target workshops.
- Onboard 5–8 willing participants as beta nodes.
- Track time-to-first-signed-event for each.
- Conduct dispute protection resonance conversations during onboarding.
- Deploy initial vehicle-centric public verification pages.
- Begin passive vehicle history accumulation.

**Decision gate at Day 30:**
- Is at least one workshop signing events consistently?
- Is the onboarding flow producing first events within the target threshold?
- Are there blocking objections appearing in outreach conversations that require pitch revision?

If zero workshops are signing events by day 30, cycle 2 cannot proceed as designed. Diagnosis required immediately.

---

### Cycle 2 — Days 31–60: Persistence Testing and Owner Discovery

**Objective:** Determine whether workshop signing behavior is durable. Begin testing owner discovery mechanism.

**Activities:**
- Continue monitoring signing frequency for all onboarded workshops.
- Flag any workshop with declining event frequency and conduct structured diagnostic conversation.
- Identify vehicles with accumulated node-signed history and no owner claim.
- Deploy owner notification flow for 10–15 unclaimed vehicles.
- Begin transaction probes: identify 3–5 secondary market transactions to observe.
- Collect first iteration of transaction probe data.

**Decision gate at Day 60:**
- Is workshop signing behavior stable or declining across the cohort?
- Has at least one owner claimed a vehicle after receiving history notification?
- Are transaction probes generating any useful qualitative data?

If workshop signing has materially declined by day 60 without a clear recoverable cause, kill criterion 2 may be approaching. Escalate assessment.

---

### Cycle 3 — Days 61–90: Persistence Confirmation and Threshold Assessment

**Objective:** Accumulate final evidence against all validation thresholds. Make go/no-go decision.

**Activities:**
- Final 30-day signing frequency measurement for all workshops.
- Complete remaining transaction probes (target total: 5–10).
- Compile full owner claim and post-claim engagement data.
- Conduct structured exit interviews with any workshop that stopped signing.
- Draft preliminary signal integrity assessment: are the events produced structurally consistent and manipulation-resistant in observed practice?
- Compile full evidence summary against each validation threshold.

**Decision gate at Day 90:**
- Have validation thresholds 1–5 been met?
- If not, which specific kill criteria apply?
- If partial, what is the precise diagnosis and what minimal additional evidence is required before MVP build?

---

## 8. What This Plan Does Not Validate

This 90-day plan is scoped to validate the behavioral assumptions underlying early adoption. It does not validate:

- **Institutional demand.** This is a Phase 3 event. No meaningful institutional validation is expected or targeted in 90 days.
- **Report revenue.** The Official Vehicle Report is not being monetized in this window. It is being structurally designed, but transaction-grade revenue is not a 90-day expectation.
- **Signal recognition at scale.** Coverage density at scale cannot be validated in 90 days. The objective is to validate that the supply-side mechanism works, not that it has reached recognition.
- **Competitive response.** The plan does not attempt to map or test competitor reaction. It is too early for that signal to be meaningful.

Attempting to validate these things in 90 days would produce noise, not signal. The plan is scoped to what can actually be tested in this window.

---

## 9. Operating Discipline

### On Data Interpretation

The most dangerous outcome is misreading weak evidence as validation. Workshops expressing enthusiasm in a conversation is not validation. A single owner claiming a vehicle is not validation. One transaction where history was mentioned is not validation.

Each threshold is defined to prevent this. The plan must be evaluated against thresholds as written — not against the best-case reading of ambiguous evidence.

### On Founder Involvement

Any signing behavior that requires regular founder prompting to sustain is not validated behavior. It is managed behavior. The thresholds are defined against autonomous adoption. The plan must actively test whether workshops sign events when the founder is not watching, not just when they are.

### On Negative Evidence

Negative evidence — workshops that do not adopt, owners that do not engage, transactions where history is irrelevant — is as valuable as positive evidence. The temptation to explain it away must be resisted. Every instance of non-adoption deserves a structured diagnosis, not a rationalization.

### On Iteration Within the 90 Days

Tactical adjustments to the pitch, onboarding flow, or owner notification approach are expected and appropriate within cycles. Strategic adjustments to the core thesis — the event model, the signing authority model, the credibility gradient — are not within scope. If 90-day evidence suggests strategic-level changes are required, that is a kill or restructure signal, not an iteration signal.

---

## 10. Output of This Plan

At day 90, the output is a single structured assessment document covering:

1. Evidence state against each hypothesis (H1–H5).
2. Evidence state against each validation threshold (1–5).
3. Whether any kill criteria have been triggered.
4. If proceeding: specific unresolved risks to carry forward and monitor in MVP phase.
5. If not proceeding: precise diagnosis of which assumptions failed and what evidence would be required to revisit.

This document becomes the foundation for the MVP PRD brief or the project restructure decision.

---

*Document 06 — 90-Day Validation Plan v1.0 | Internal Use Only*
