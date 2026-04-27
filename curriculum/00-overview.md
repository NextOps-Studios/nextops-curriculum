# Curriculum Overview — v1 Complete

## Principle

**The full startup curriculum ships in v1.** Different in-game businesses (spaza → salon → taxi rank → scrapyard → gas reseller → robotics club) stagger across releases as expressions of the same fundamentals. A player who finishes the v1 spaza arc has been exposed to every concept in the stack.

The curriculum is organized as **eight pillars**, each with sub-concepts. Every sub-concept maps to at least one in-game mechanic. If a concept can only be taught via tutorial copy or a quiz screen, it gets cut.

---

## The eight pillars

### 1. Problem-solving
- First-principles thinking
- Root-cause analysis (why did the spaza fail this week?)
- Decomposition (break a big problem into small ones)
- Pattern recognition (this customer pattern repeats)
- Iteration under feedback (try, measure, learn)
- Debugging (your inverter isn't working — diagnose)

### 2. Critical thinking
- Decision under ambiguity (which inverter to buy with imperfect info?)
- Steelmanning (what's the strongest case AGAINST your plan?)
- Identifying assumptions (what does this plan assume? What if it's wrong?)
- Cost-benefit reasoning
- Avoiding sunk-cost fallacy
- Distinguishing signal from noise

### 3. Lean startup / customer discovery
- Get out of the building (talk to NPCs first)
- The Mom Test (specific past behavior > general future intent)
- Problem-solution fit (per-district product preferences)
- Product-market fit (which spaza format works in which district)
- Build-Measure-Learn (Day Report)
- Pivot vs. persevere (when sales flatline, what changes?)
- Minimum viable product (start tiny — you only have R500)

### 4. Business model fluency
- Revenue streams: one-time vs. recurring
- Subscription model (Mama Thandi pays R50/week for delivery)
- Bundle pricing (combo meals)
- Loyalty programs (regulars get -10%)
- Reseller model (gas, airtime, electricity vouchers)
- Marketplace (taxi rank — two-sided)
- Service-as-a-product (salon appointments)
- Capex-as-opex (solar lease, inverter rental)
- Co-operative finance (stokvel = ROSCA)
- Commodity arbitrage (scrapyard)

### 5. Unit economics + capital efficiency
- Cost of goods sold
- Gross margin per product
- CAC (cost to acquire a customer — what marketing brought them?)
- LTV (lifetime value — how much will Mama Thandi spend over 6 months?)
- Cash flow vs. profit (slate / extending credit)
- Runway (how many in-game months can you survive at this burn?)
- Reinvestment vs. distribution

### 6. Technology fundamentals (staggered into the gameplay across v1 → v6)
- **v1:** QR scanning at checkout, basic POS, signage as branding
- **v2:** Booking systems (salon), SMS reminders, calendar logic
- **v3:** GPS routing (taxi rank), surge pricing algorithm
- **v4:** IoT weight sensors (scrapyard), computer-vision sorting
- **v5:** Gas-fill sensors (reseller), leak detection, remote monitoring
- **v6:** Robotics club — players literally wire blocks, write code blocks, deploy bots that run challenges

Every tech concept is introduced through **need**: the spaza needs a POS, the salon needs a booking system, the scrapyard needs sensors. Tech is never abstract; it's always solving a problem the player just felt.

### 7. People & ops
- Hiring your first staff (3 candidates with different strengths — choose)
- Training, delegation, accountability
- Negotiation (wholesaler bargain mini-game)
- Conflict resolution (NPC complaint → handle it)
- Building a network (district reputation)
- Storytelling / pitch craft (the brand-partnership pitch arc with NPC banks)

### 8. Ethics, resilience, identity
- Should you extend credit to the kid who can't pay back?
- The "load shedding catastrophe" — recover or fold?
- Selling out vs. staying authentic (the "big brand wants to buy your spaza" arc)
- Failure as data, not shame (the failed-spaza-graduation flow)
- Ubuntu — your stokvel community is your safety net
- Long-term thinking (your kids will inherit this — what do you build for them?)

---

## Mapping the eight pillars to v1 mechanics

Every gameplay system in v1 must touch at least 3 pillars. The cross-walk:

| v1 mechanic | Pillars touched |
|---|---|
| Customer dialogue (Mom Test) | 1, 2, 3, 7 |
| Day Report (BML loop) | 1, 3, 5 |
| Per-district stocking | 2, 3, 4 |
| Stokvel | 2, 4, 5, 8 |
| Pricing UI (margin warnings) | 1, 5 |
| Pivot-or-persevere events | 1, 2, 8 |
| Random crisis events (load shedding, taxi strike, funeral) | 1, 2, 8 |
| Hiring NPC staff | 7, 8 |
| Wholesaler negotiation | 4, 5, 7 |
| Brand partnership pitch (NPC bank) | 4, 7, 8 |
| QR / POS introduction | 6, 4 |
| Graduation / sell-and-restart | 5, 8 |
| Founder Pass (free track = full curriculum) | All 8 (parallel reinforcement) |

Coverage check: every pillar appears in ≥ 4 mechanics. No pillar is teaching-on-rails — every pillar is reinforced by 4+ different gameplay surfaces.

---

## Real-world bridge (the "Pokémon GO–style" layer)

Founder Mode is not just a game. The curriculum's load-bearing claim is **real-world transfer** — concepts learned in-game must apply to actual life. Hooks designed in:

| Bridge | v1 ships | Full vision |
|---|:---:|---|
| **Real-world challenges tab** — weekly offline tasks ("visit a real spaza, ask the owner what their best-selling product is, photograph it, post on TikTok with #foundermode") | ✅ honor system | v2: photo upload + verification |
| **Companion mobile app** | ❌ | v3+: full app with QR scan, real-stokvel logbook, AR overlays |
| **AR overlay on real signage** | ❌ | v4+: scan a real spaza sign, get an in-game easter egg + real-life entrepreneurship tip |
| **Real stokvel tracker** | ❌ | v3+: log your real stokvel rotation in the app, sync to in-game stokvel for compounded learning |
| **IRL meetups / pop-ups** | ❌ | v2+: SA city pop-ups where players come run real spaza simulations + meet successful kasi entrepreneurs |
| **In-game cosmetics earned by real-world actions** | ✅ honor system | v2+: photo verification |
| **NPC dialogue references real businesses player documented** | ❌ | v3+: app → game pipeline |
| **Hardware kit companion** (robotics) | ❌ | v6+: physical Arduino-equivalent kit shipped with code-blocks that bridge in-game robotics to real Arduino projects |

The real-world bridge is **multi-year**. v1 ships the philosophical commitment + the lightest hook (real-world challenges tab with honor-system rewards). The full Pokémon-GO–style integration is a 3-5 year roadmap. Naming it now ensures every v1 design decision keeps the door open.

---

## Pedagogy design rules (the "never feels like learning" laws)

These rules are non-negotiable. They override every other design impulse.

1. **No tutorial that teaches a concept.** If a concept can only be taught by exposition, the mechanic has failed. Concepts surface through consequence, not copy.
2. **No quiz screens.** Ever. The game does not test the player; the player's results test the player.
3. **No "education mode" toggle.** The game has one mode. Pedagogy is the architecture, not a feature flag.
4. **No "this is what you learned today" moralizing.** The Day Report shows data, not lectures.
5. **Marketing copy never uses "educational," "learn," "teaches," "school," "curriculum."** External-facing language is "tycoon," "build your empire," "kasi life," "founder mode."
6. **The game is fun before it is meaningful.** If a frustrated playtester says "this isn't fun," that beats "this isn't pedagogically rigorous." Fix fun first.
7. **Cultural authenticity > pedagogical rigor when they conflict.** A culturally inauthentic but lesson-perfect mechanic gets cut. A culturally authentic but lesson-fuzzy mechanic gets refined, not deleted.
8. **The pedagogy is the moat from a partnership perspective; never from a player perspective.** The FNB/Capitec/Yoco pitch deck cites the eight pillars. The TikTok caption never mentions them.

---

## Maintenance

This document is the v1 spine. The curriculum agent (running daily) deep-dives ONE concept per day under `concepts/`. Over ~6 months the agent will build a complete, peer-reviewed deep-dive library covering every sub-concept above.

Human review of the agent's daily output is async — review when convenient, edit when warranted. The agent never auto-merges; every concept deep-dive opens a GitHub issue tagged `curriculum-review` for the human to close.
