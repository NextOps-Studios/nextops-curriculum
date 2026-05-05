---
concept: Unit Economics — LTV, CAC, Gross Margin
pillar: 5
status: approved
created: 2026-05-05
agent_run_id: human-seed-004
sources_verified: yes
---

# Unit Economics — LTV, CAC, Gross Margin

## What it is (90-second version)

Unit economics is what happens when you stop thinking about your business as a single big number ("we made R10,000 last month") and start thinking about it as a series of identical small ones ("we made R8 per customer, and we have 1,250 customers"). Every business — spaza, SaaS, Quantum, salon — is just a customer-count multiplied by a per-customer profit. If the per-customer math doesn't work, scaling makes things worse, not better.

Three numbers carry the whole framework:

1. **Gross Margin** — what you keep per sale after paying the cost of what you sold. (R5 bread sold for R12 = R7 gross margin = 58% margin.)
2. **CAC (Customer Acquisition Cost)** — what you spent to get this customer through the door. Marketing spend, signage cost, sponsorships divided by customer count.
3. **LTV (Lifetime Value)** — total gross margin you'll earn from one customer over the entire time they remain a customer. Mama Thandi who comes daily for 18 months and spends R8 margin each time = R4,400 LTV.

The single rule: **LTV must exceed CAC by at least 3x for the business to scale healthily.** If you spend R100 on signage and the average customer that signage brings in delivers R30 lifetime margin, scaling kills you. If they deliver R400, scaling makes you rich.

## Why it matters

Most failed businesses didn't fail at the level the founder thought they did. The founder thought they failed at "growth" or "execution" or "marketing." The unit economics — ignored or unmeasured — were already dead. Growing a business with negative unit economics just means losing money faster.

This is sharper in SA + African contexts because:
- Margins on real spaza shops average 8-15% (not 50% like SaaS). Tiny error margins, no buffer for waste.
- "Loyalty" isn't a feel-good word — it's the only thing turning a 15% one-time-margin into the multi-year LTV that pays the rent.
- Every cent of CAC is felt directly (you painted that signage with cash you needed for stock).

A founder who internalizes unit economics asks "what's my CAC?" before "how do I market?" — and that order saves them.

## Real-world examples

**Yoco's first 100 customers, 2015.** Yoco's CAC at small-business expos was ~R200 per converted customer (booth costs + travel + on-site sales). Each merchant they signed up paid Yoco a per-transaction fee averaging R40-60 per month gross margin. Average merchant retention at that stage was 14 months. LTV ≈ R700 → LTV/CAC ratio of 3.5x. They were healthy. By 2020, paid-acquisition channels pushed CAC up to ~R400 but LTV had grown to ~R3,000 (longer retention + higher per-merchant volumes). Ratio: 7.5x. That ratio is why they could raise.

**Adopt Me's pet economy.** DreamCraft (Uplift Games) ships pets that retain players for years. Average paying-player ARPU is reported around $7/month, retention is multi-year, so LTV is in the $200-400 range. Roblox creator-economy CAC is approximately $0 (Roblox's own discovery surface drives traffic). LTV/CAC is functionally infinite. That's why the game makes $60M/year. Every Roblox tycoon developer who copies the visible-progress dopamine without copying the high-LTV pet economy ends up with the visible loop but nothing for it to sustain.

**Failure case: a SA fintech that died at 12,000 users.** Documented in *Daily Maverick*, 2022 (anonymized post-mortem). The fintech built a slick app and acquired 12,000 SMB users at R350 CAC each via Facebook ads. Average user delivered R8/month margin and churned at month 4. LTV: R32. LTV/CAC: 0.09x — every customer cost R318 net. At 12,000 users they had burned R3.8M and were still scaling acquisition because users were "growing." Revenue grew; cash declined faster. Liquidation in month 18. The unit economics were dead from day 100; the founders didn't measure them until month 14.

## In-game expression — Founder Mode mapping

This concept fires through TWO server systems running in tandem.

### 1. The repeat-customer loyalty system (Pillar 5 LTV carrier)

`namedRegulars` records on the player's profile (see `Types.luau`) capture per-NPC `loyalty`, `lastPurchase`, `totalLifetimeSpend`, `preferredProducts`. Every successful sale to a named regular increments their `totalLifetimeSpend`. The Idle system (`Systems/Idle/init.luau`) scales offline revenue per regular by their loyalty: `revenue = rate × offlineDays × (1 + loyalty/100)`.

Players see this play out: Mama Thandi at 80 loyalty is generating R30 × (1 + 0.80) = R54/real-day in offline revenue. Mama Thandi at 0 loyalty (fresh, never talked-to) generates R30. The 80-point loyalty difference is **directly visible as a 80% LTV uplift**. The math is the lesson.

### 2. The signage-vs-revenue trade (Pillar 5 CAC carrier)

`SpazaItems.luau` includes `signageStrength` per signage item. The hand-painted wall sign costs R120 and provides 5 strength. The LED board costs R1,200 and provides 9 strength (but requires power, so load shedding kills it).

Signage strength feeds into the customer-arrival rate (v0.2 wires this into NPC.luau). A player with 0 signage and a player with 18 signage strength see different arrival counts. The player can math out: "I spent R1,200 on the LED board; my arrival rate increased by 15%; my margin per customer is R7; so I need 171 more customers before the LED board pays back."

That's CAC math, in-game, kasi-styled. The player doesn't see the words "CAC" or "payback period" — they see the cost, the customers, and the time-to-break-even.

### Why it lands the lesson

A player who plays for ~6 hours has run roughly 7 in-game days. By day 7 they've watched:
- A loyal regular (Mama Thandi at 80 loyalty) generate R400 over the week vs.
- A non-loyal walker-by generate R12 once

That's 30x LTV difference, observable, in their own ledger. They internalize "loyalty is the asset" without ever reading the words "lifetime value." When they later study LTV in school or a Coursera course, they recognize their own spaza's numbers in the math.

### Cross-link

This concept compounds with:
- **Customer Discovery** (the Mom-Test gold dialogue is what BUILDS loyalty in the first place)
- **Pivot vs Persevere** (a 7-day ignored unmet-want is killing your LTV by killing retention)
- **Day Report** (revenue + profit columns ARE unit economics laid out daily)
- **Capital Pooling / Stokvel** (the stokvel payout is a CAC-financed jump — buy the bigger fridge, increase margin, pay back the stokvel pot through better unit economics)
- **Prestige / Graduation** (resetting the spaza preserves named regulars — your accumulated LTV isn't lost when you graduate; that's the lesson on relationship capital)

## Real-world bridge

A player who has internalized "loyalty is the asset" can apply it the same week:

- **Real-world challenge unlock:** "Visit a real spaza near you. Watch for 30 minutes. Count how many customers walk in (total) vs. how many were greeted by name (loyal regulars). Submit the ratio on Founder Mode TikTok with #spazaltv. In-game cosmetic reward."
- **Career application:** Anyone joining a startup, an ad agency, a consultancy, or a bank has been pre-trained to ask "what's the LTV here?" — instead of "what's the revenue?" — by hundreds of in-game iterations. They show up sounding three years more senior than they are.
- **Side-project application:** A 14-year-old running a sneaker resale flip has been trained to track per-buyer profit, not per-shoe profit. They notice that one buyer who buys 5 pairs/year is worth more than 5 buyers who buy 1 pair each.

## Pedagogy notes (for the design team)

- The `1 + loyalty/100` multiplier in the Idle system is the central pedagogy lever. Tweak too high → grinders dominate, talk-first matters less. Tweak too low → talking is cosmetic. v1 starts at +100% at full loyalty; playtest.
- Day Report MUST keep showing per-product revenue (currently aggregated). A future v0.2 should add per-customer revenue ranking ("your top 5 regulars contributed 40% of revenue this week"). That's a direct LTV table without the words.
- The signage-vs-arrival math IS the lesson; never auto-calculate "payback days remaining" for the player. Let them figure it out. The math being visible-but-uncomputed is the pedagogy.
- Brand-partnership pitch deck for FNB / Capitec / Yoco: "we teach 9-year-olds unit economics through a game" is a sentence that lands extremely hard with banks and fintechs. Lead the conversation here.

## Open questions for human review

1. **Should the Day Report add a per-customer ranking column?** (See pedagogy note above.) v0.2 candidate; pedagogy says yes, UX says careful.
2. **What's the "right" loyalty cap for v1 — 100 or higher?** A higher cap (200, infinite) creates a forever-grinding loop. 100 caps and forces players to invest in NEW relationships once existing ones are maxed. Pedagogy is on the 100 side: real businesses can't infinite-loyalty a single customer, they have to find more.
3. **Should we surface the LTV math anywhere?** A "Spaza Plan" UI panel (currently cut from v1) would show it. Cutting again from v0.2; v1.1 brings it back as a cosmetic Game Pass unlock (per the Retention Spine v1.1 cuts table).

## Sources

- David Skok, *SaaS Metrics 2.0* — for SaaS LTV/CAC; framework generalizes
- Bill Gurley, *The 3x LTV/CAC rule* — Above the Crowd blog
- Yoco founder talks (TechCabal interviews 2018-2024) for the early-stage CAC numbers
- *Daily Maverick* 2022 SA fintech post-mortem — anonymized, pattern documented
- Adopt Me revenue figures — Bloomberg + GamesIndustry.biz coverage 2022-2024

---

This concept is the FOURTH seed exemplar for the Curriculum Agent. Together with `customer-discovery.md`, `build-measure-learn.md`, `capital-pooling-rosca.md`, the agent now has four-pillar coverage of the quality bar.
