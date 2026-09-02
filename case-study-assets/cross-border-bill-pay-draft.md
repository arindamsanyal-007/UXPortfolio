# Case Study Draft — Global Cross-Border Bill Pay

*Draft for portfolio review — trim/tighten before publishing as a case-study page.*

---

## Working Title
**Cross-Border Bill Pay** — Turning remittance into direct, purpose-built bill payments

## Tags
`Design Strategist` · `Design Lead` · `Fintech` · `0→1 Product`

## Role
**Design Strategist & Lead** — owned the end-to-end UX strategy and design leadership for the initiative: framed the opportunity, defined the vision narrative and guiding principles, led the competitive analysis, designed the core flows and high-fidelity prototype, and partnered with Product, BILRS (partner integration), Compliance, and Engineering to shape the phased roadmap.

---

## One-line Summary
Migrants and expats send ~30% of their remittances toward bills back home — through indirect, fragmented processes. I led the UX strategy and design for Western Union's first direct **Cross-Border Bill Pay** experience, replacing a legacy, low-adoption product (Quick Pay) with a modern, biller-network-backed flow — piloting in the E1 Canada app with a clear path to scale globally.

---

## The Problem
Remittance was being used as an indirect bill-payment mechanism, creating friction on both ends:
- **Senders** had no way to pay a bill directly — they had to trust receivers to complete payment after funds landed.
- **Receivers** relied on manual, cash-based, or fragmented local processes, often missing due dates.
- Neither side had visibility into *whether* or *when* a bill was actually paid — low transparency, low trust.
- A prior attempt (**Quick Pay**, built on the U.S. Quick Collect framework) failed to scale due to a cumbersome biller-setup process and weak UX.

**Opportunity:** ~$170B in addressable transaction volume globally, ~$25–30M in annual revenue potential — concentrated in corridors like US→Mexico, US→India, and UAE→Philippines.

---

## Business Goals
*(from presentation deck)*
- Capture a $25–$30M annual revenue opportunity (2-year projection)
- Position Western Union as a market leader in cross-border bill pay
- Deliver a secure &amp; transparent, end-to-end bill pay experience
- Position bill pay as a high-frequency, essential service (not a one-off transaction)
- Build a scalable, global bill pay capability
- Drive organic revenue growth

---

## My Approach

**1. Reframed the problem as a strategist**
Rather than treating bill pay as a remittance add-on, I reframed it as its own first-class journey — "pay the bill directly," not "send money and hope." This reframing anchored every downstream design decision.

**2. Competitive & experience benchmarking**
Ran a structured competitive teardown across global players (Wise, Xoom by PayPal, Careem Pay, Comera Pay) and Canada-specific bill-pay products (PaySimply, Beacon) to define what "best-in-class" looks like: comprehensive global biller coverage, a simple/fast/trusted experience, low cost and risk for users and billers, localized payment options, simpler biller onboarding, robust reconciliation across countries, and risk &amp; compliance built into the flow — not bolted on after.

**3. Grounded the vision in real personas**
Built 5 scenario narratives (the migrant worker, the student abroad, the supporting sibling, the busy professional, the underbanked receiver) to pressure-test the design against real emotional and situational friction — not just transactional steps.

**4. Defined 4 design principles for a scalable platform**
*(from presentation deck, replacing the earlier 7-principle draft)*
1. **Radical transparency** — fees, FX, and due dates visible before checkout, always
2. **Purpose-built flows** — designed for bill pay as its own journey, not a remittance afterthought
3. **Sender–receiver collaboration** — both sides of the corridor stay informed and in sync
4. **Built to scale, tailored locally** — one global architecture, adapted per market and corridor

**5. Designed the core end-to-end flow**
Led the wireframes and high-fidelity Figma prototype across **two key journeys** — the first-time user (never paid bills via WU) and the returning user (has paid before) — covering: country/biller selection → bill discovery &amp; linking → transparent fee/FX breakdown → localized pay-in methods → confirmation, tracking, and reminders.

**6. Partnered across the org**
Worked directly with Product on objectives/hypotheses, BILRS/partner teams on API-driven biller catalog integration, Compliance on corridor/biller whitelisting logic, and Engineering on a phased delivery roadmap (Phase 1 → 3).

---

## Key Design Decisions
- **Transparency-first checkout:** every screen shows bill due amount, FX rate, fee breakdown, and total — before the user commits.
- **Progressive biller discovery:** search/filter by country, category, and biller name, with clear empty states — designed to scale to thousands of billers without added complexity.
- **Two tailored onboarding paths:** distinct flows for first-time vs. returning users, so repeat payers aren't slowed down by setup steps they've already completed.
- **Design for the underbanked, not just the digital-native:** included an OCR-based "photograph your bill" path for less tech-savvy users (see: Lucía &amp; Rio scenario).
- **Compliance embedded, not bolted on:** corridors and biller types are filtered at the front end based on Risk &amp; Compliance whitelisting — invisible to the user, but critical to the architecture.

---

## Phased Roadmap
*(from presentation deck)*

**Phase 1 — Baseline experience**
- Pay a new bill, for new &amp; existing users
- Bill Pay homepage
- Bill search, selection, fetch &amp; pay (domestic &amp; cross-border)
- Bill Pay transaction history + track a transfer
- FAQs
- Loyalty program

**Phase 2 — Advanced bill management**
- Auto-fetch of new bills for existing users (based on prior payment details), with proactive notification
- AutoPay — invoke users to set up recurring payments
- Gmail/SMS read access (one-time consent) to auto-fetch bills from issuer emails

---

## Outcomes / What Success Looks Like
*(Framed as hypotheses at time of writing — update with real metrics post-launch)*
- ≥10% of eligible users complete a cross-border bill payment within 90 days of onboarding
- ≥40% increase in repeat bill payments via saved billers
- >25% improvement in repeat payment rate via predictive reminders & autopay nudges
- North Star: number of bills paid per month (domestic + international)

---

## Suggested Visuals to Pull from Figma
*(from [UXD-2261 | Global E1 | Cross-Border & Domestic Bill Pay](https://www.figma.com/board/MSz3SxgAaOn2vyWhlJZmVI/UXD-2261-%7C-Global-E1-%7C-Cross-Border---Domestic-Bill-Pay?node-id=1205-1233629))*
1. Vision/scenario board (the 5 personas) — great for storytelling opener
2. Competitive benchmarking snapshot — shows strategic rigor
3. Core flow: biller search → selection → bill fetch → fee breakdown → confirmation
4. Guiding principles summary slide (if visual)

---

## Notes for Final Case Study Page
- Keep it to 4–5 sections max: **Problem → My Role/Approach → Key Decisions → Outcomes** (matches existing case-study template structure: Send Money, UX Baseline, Content Network)
- Lead with the "Ravi" or "Ana" scenario as a 2-line human hook before the metrics
- Emphasize **strategist + lead** framing explicitly in the role/tags — this project is a stronger "strategy" story than the other case studies, which lean more execution-heavy
- Confirm public-safe framing: strip internal codenames (BILRS, DIGITAL-1293, PSTLMNTJC-859) and any Jira/BRD links before publishing
