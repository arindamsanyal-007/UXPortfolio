# UX Portfolio Case Study Content Plan
**Owner:** Arindam Sanyal — Product Design Manager  
**Target roles:** Design Manager, Principal Product Designer, Head of Design  
**Last updated:** 2026-07-09

---

## Portfolio Story Arc

Each case study should build a different facet of the leadership argument:

| Case Study | Core leadership argument |
|---|---|
| WU E1 Redesign | I can lead large, complex, regulated product redesigns at scale |
| UX Baseline | I build the infrastructure that makes design teams permanently better |
| Send Money IMT | I drive interaction quality and accessibility without compromising velocity |
| Content Network | I think in product strategy, not just product design |

Together they answer: *"Can this person lead design at the highest level in a global fintech context?"*

---

## Case Study 1 — WU E1 Redesign
**File:** `wu-redesign-case-study.html`  
**Status:** ✅ Draft complete — needs real screenshots + metrics validation

### Hook
> Unified 5 fragmented digital products into one wallet-based platform — the biggest redesign in Western Union's history.

### Context to write
- Western Union: 150+ year old financial institution, 200+ countries
- E1 = the new unified app (replacing R3, R4, US Wallet, EU Banking App, CA app)
- Team: 11 designers, 40+ engineers, compliance, content, brand
- Constraint: KYC/AML regulations across 6+ markets

### Problem to frame
- 5 apps, 5 stacks, duplicated effort, inconsistent user trust signals
- Move-to-account-based model was a business imperative, not a UX preference
- Engineering was already scaled; design was the bottleneck

### Process decisions to cover (pick 3)
1. Design system before production screens — the case made, the 3-week delay justified
2. Dual-track agile introduction — how it was sold to engineering and PM
3. RICE prioritisation for epic sequencing — why we used it, what it changed

### Metrics to include
- 40% rework reduction (via design QA rituals)
- ~5% drop-off reduction across key journeys
- ~20% faster design-to-engineering handoff
- 142+ screens shipped at consistent quality

### Images needed
- Payments hub (✅ 03-payments-hub.png)
- Transfer flow (✅ 05-send-with-contacts.png, 04-send-methods.png)
- End-to-end flow (✅ 08-bank-account-flow.png)
- [ ] Design system overview screenshot (missing)
- [ ] Before/after IA comparison (missing)

### Retrospective angle
> I'd build research ops infrastructure earlier. Research existed but wasn't findable — designers were duplicating work by month 6.

---

## Case Study 2 — The Case for a UX Baseline
**File:** `ux-baseline-case-study.html`  
**Status:** 🔴 Content not yet written — placeholder page only

### Hook
> Established the first shared UX standards at Western Union — turning a 30-person siloed design org into a coherent, measurable practice.

### Context to write
- Post-E1: design org growing, inconsistency increasing
- No shared patterns, no handoff standards, no quality bar
- Multiple markets, multiple product squads, no alignment

### Problem to frame
- Design was scaling in headcount but not in quality or consistency
- Engineers making UI decisions because design specs were incomplete
- No way to measure "good design" across squads

### Process decisions to cover
1. Defining what "baseline" means — the negotiation with PM and Eng leadership
2. Audit methodology — how we measured the existing gap
3. Adoption strategy — how we got 30 designers to actually use it

### Metrics to include (need to gather)
- [ ] % reduction in design-related bug reports post-baseline
- [ ] Time to onboard new designers (before/after)
- [ ] Consistency score across audited product areas
- [ ] Number of patterns standardised

### Images needed
- [ ] Before/after audit comparison
- [ ] Baseline documentation overview
- [ ] Adoption curve / rollout timeline
- Currently placeholder: 03-payments-hub.png (replace)

### Retrospective angle
> The baseline addressed surface inconsistency but not root cause — different squads had different interpretations of user needs. I'd pair the standards work with a shared research repository next time.

---

## Case Study 3 — Send Money IMT
**File:** `send-money-imt-case-study.html`  
**Status:** 🔴 Content not yet written — placeholder page only

### Hook
> Redesigned Western Union's core transfer flow — reducing perceived steps from 7 to 3 while meeting WCAG 2.1 AA across 6 markets.

### Context to write
- Core product: international money transfer
- Used by millions of senders monthly across mobile and web
- Constraint: regulatory disclosure requirements, accessibility mandates
- 40+ engineer dependency, 3 squads involved

### Problem to frame
- Existing flow was corridor-first ("where are you sending?") not person-first
- 7-step mental model didn't match how users actually thought about sending money
- Accessibility was bolted on after — failing WCAG in 12+ components

### Process decisions to cover
1. The person-first vs corridor-first IA decision — research that drove it
2. Fee transparency design — the compliance vs UX tension and how it was resolved
3. Accessibility integration — shifting from retrofit to design-first

### Metrics to include (need to gather)
- [ ] Drop-off reduction at each step
- [ ] Accessibility audit score improvement
- [ ] Task completion rate (usability testing)
- [ ] Engineering rework reduced from accessibility issues

### Images needed
- ✅ 01-hero-send-money-imt.png
- ✅ 02-new-recipient-flow.png
- ✅ 05-send-with-contacts.png
- ✅ 07-send-from.png
- [ ] Before/after flow comparison

### Retrospective angle
> We validated the person-first IA in testing but launched too fast on the fee transparency module — it still caused confusion in markets with complex fee structures. I'd have done a second round of testing in high-complexity corridors before launch.

---

## Case Study 4 — Content Network Product Strategy
**File:** `content-network-case-study.html`  
**Status:** 🔴 Content not yet written — placeholder page only

### Hook
> Defined the UX strategy for Western Union's personalisation platform — shifting the product from a transaction tool to a financial relationship.

### Context to write
- Post-E1 product expansion: move beyond core transfer
- Content Network = personalised financial content, offers, loyalty
- First time design was involved at product strategy level (not execution)
- Stakeholders: Chief Product Officer, Marketing, Data Science

### Problem to frame
- WU was losing digital engagement to apps with richer financial relationships
- Loyalty programme existed but wasn't integrated into the core experience
- No design language for "content" that felt native to a money transfer app

### Process decisions to cover
1. Design's seat at the product strategy table — how it was earned
2. Defining the personalisation model — balancing data use with user trust
3. Content component system — extending E1 design system for editorial content

### Metrics to include (need to gather)
- [ ] Engagement rate with personalised content modules
- [ ] Cross-sell / upsell conversion from content
- [ ] Session depth increase
- [ ] Loyalty activation rate

### Images needed
- ✅ 06-send-to.png (reuse for now)
- [ ] Personalisation framework diagram
- [ ] Content component library overview
- [ ] Before/after engagement data visualisation

### Retrospective angle
> The design was strong but the data infrastructure wasn't ready. We shipped a personalisation UI that showed the same content to everyone for the first 6 weeks because the ML pipeline was delayed. I'd have tied design delivery to data readiness, not the engineering sprint calendar.

---

## Shared Writing Rules (Apply to All 4)

1. **Max 700 words per case study** — if it's longer, cut, don't compress
2. **Every metric in a table** — label, before, after, business meaning
3. **Role table on every page** — 2 columns: what I owned vs what the team delivered
4. **One retrospective per page** — 60–80 words, specific, honest
5. **No screen inventories** — "47 screens" is not a metric
6. **Captions answer "so what?"** — not "what is this screen showing"
7. **Section labels are outcomes** — not "Research" but "What we discovered"

---

## Content Gathering Checklist

Before writing/finalising each case study, gather:

### From memory / experience
- [ ] Key decisions made and alternatives rejected
- [ ] Stakeholders involved and how alignment was reached
- [ ] What changed in team process as a result of this work
- [ ] What was hardest and why

### From data / metrics
- [ ] Any analytics dashboards (Amplitude, Quantum Metrics)
- [ ] Usability testing results / task completion rates
- [ ] Accessibility audit scores (before/after)
- [ ] Sprint velocity change (if tracked)
- [ ] NPS or CSAT data

### From artefacts
- [ ] Final design screens (Figma links or exports)
- [ ] Research reports or synthesis documents
- [ ] Design system documentation
- [ ] Before/after IA or flow comparisons

---

## Priority Order

1. **WU E1 Redesign** — strongest material, most complete ✅
2. **Send Money IMT** — core craft + accessibility story, good for IC leadership
3. **UX Baseline** — highest signal for Design Manager roles
4. **Content Network** — strongest signal for strategic/CPO-adjacent roles

Write 2 and 3 next. Start with the hook for each before writing full content.
