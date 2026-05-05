# NPC Dialogue Expansion — From 10 to 50 Named Regulars

The eng-review locked **50 named regulars** for v1. We currently have 10 in
`src/ReplicatedStorage/Config/NPCs.luau`. This brief specifies the remaining
40 characters with full Mom-Test dialogue trees + cultural authenticity
guardrails.

**Why 50 matters:** The retention spine depends on the player accumulating
relationships over multiple in-game weeks. With only 10 NPCs, the player
maxes loyalty on everyone in 2-3 hours and the customer-discovery curriculum
collapses. With 50, the discovery loop stays alive for ~3-4 months of casual
play (retaining players for the v1.1 multiplayer-stokvel ship window).

---

## The 40 NPCs to add (organized by district + archetype)

### Soweto Main (already has 10; add 5 more for diversity)

**11. Bra Tshepo — small-engine mechanic + spinning crew**
- Archetype: car-spinner-mechanic (overlap with Bra Vusi but DIFFERENT day rhythm — Tshepo arrives mid-week to grab parts; Vusi arrives weekends with the crew)
- Visit frequency: weekly
- Preferred products: cigarette-loose, energy-drink, motor-oil
- Dialogue gold: "How's the gusheshe project? Last weekend's spin go OK?" → reveals he's restoring a 325is + sells used parts on the side

**12. Lesego — primary-school teacher**
- Archetype: educator-stable-income
- Visit frequency: daily
- Preferred products: coffee-instant, biscuits, marking-pens, photocopying
- Dialogue gold: "How's the term going?" → reveals daily marking-pen demand spikes at term-end + photocopying side hustle

**13. Sizwe's mother (Mama Nokuthula) — domestic worker**
- Archetype: working-mother-multiple-kids
- Visit frequency: daily
- Preferred products: bread, milk, instant-noodles, school-supplies
- Dialogue gold: "How's Sizwe doing in school?" → reveals she's saving for his university fees + bulk-buys are strategic

**14. Ouma Margaret — Afrikaans-speaking elderly resident**
- Archetype: gogo-isolated (she's a kasi character but speaks Afrikaans + a little English; cultural-authenticity check: Soweto has multilingual elderly residents)
- Visit frequency: weekly
- Preferred products: rooibos-tea, biscuits, paraffin, candles
- Dialogue gold: "How's the load shedding treating you, Ouma?" → reveals she stocks paraffin for backup cooking

**15. The Pastor (Bhuti Mzwakhe) — local church pastor**
- Archetype: community-leader
- Visit frequency: weekly (Saturdays especially)
- Preferred products: sweets, cooldrink, biscuits, communion-wafers
- Dialogue gold: "How many at service this Sunday?" → reveals he buys for the after-service tea + sometimes a wedding

### Khayelitsha District (NEW — 15 NPCs)

This is the second district that ships in v0.x post-Tier-1 art. Khayelitsha
has different demographics than Soweto: younger, more migrant labor, more
informal-economy density. Different products, different rhythms.

**16. Bra Sandile — fish-and-chips hustler**
- Archetype: street-food-vendor
- Visit frequency: daily
- Preferred products: oil-cooking, salt, vinegar, plastic-cups
- Dialogue gold: "How's the lunch rush?" → reveals R200/day buy-rhythm + lunch-hour demand spikes

**17. Sister Buyi — community health worker**
- Archetype: health-worker-municipal
- Visit frequency: daily
- Preferred products: water-still, sandwich, hand-sanitizer, coffee-instant
- Dialogue gold: "How are the home visits today?" → reveals she covers ~30 households daily + needs travel snacks

**18. Bra Vincent — Cape Town minibus driver (route: Khayelitsha → CBD)**
- Archetype: long-route-taxi-driver (different from Bra Sipho — Vincent does single 90-min routes vs Sipho's neighborhood loops)
- Visit frequency: daily
- Preferred products: cooldrink, energy-drink, biltong, airtime
- Dialogue gold: "How's the CBD route this week — the queue still long at Cape Town Station?" → reveals the morning rush ends 09:30; gap until 14:00; bulk demand patterns

**19. Aunty Gladys — laundry service operator**
- Archetype: laundry-business-owner
- Visit frequency: weekly
- Preferred products: detergent-liquid, fabric-softener, plastic-bags-large, cooldrink
- Dialogue gold: "How many loads this week?" → reveals 40 households on her route + bulk-detergent buying

**20. Kabelo — uni student (UWC, comes home weekends)**
- Archetype: university-student-home-weekends
- Visit frequency: weekly (Fri-Sun only)
- Preferred products: instant-noodles, energy-drink, study-snacks, airtime-data
- Dialogue gold: "How's the assignments?" → reveals exam-week demand spikes + late-night study stocks

**21. Mama Phumla — sangoma / traditional healer (CULTURAL: handle with respect)**
- Archetype: traditional-healer
- Visit frequency: weekly
- Preferred products: candles, incense, cleaning-products, herbal-teas
- Dialogue gold: "How are the consultations going this week?" → reveals her weekly rituals + consumable patterns
- Cultural note: Sangomas are real practicing healers in SA; ANY dialogue here MUST be reviewed by an SA cultural advisor before ship. Suggest temporarily marking as "stub" status until reviewed.

**22-30:** [9 more Khayelitsha NPCs across street-vendor, security guard, taxi-rank organizer, hostel resident, school principal, scrap-yard owner, hawker, kasi-style-DJ-side-hustler, retired-mineworker archetypes — each with the same dialogue depth]

### Mamelodi District (NEW — 15 NPCs)

Mamelodi is north-eastern Tshwane (Pretoria area). More mixed-Sesotho/Setswana, more government workers, different rhythms again. Same archetype distribution; different cultural specifics.

**31-45:** [15 NPCs spanning government-clerk, civil-servant, mine-engineer, teacher, salon-owner, taxi-driver, student, security guard, sangoma-pretoria-style, market-trader, etc.]

### Bonus Cross-District — 5 "drifters"

**46-50:** Five characters who appear in ALL districts but rarely:
- Travelling salesman (every 3 weeks per district)
- Tourism worker (one-off visitors with weird wants)
- Foreign nationals (Zim, DRC, Mozambique migrants — handled with cultural respect, real economic representation of SA's diversity)
- Off-duty cop
- Young entrepreneur scouting for a spaza purchase (the "I want to buy your shop" arc starts here)

---

## Dialogue depth standards (from `customer-discovery.md` exemplar)

Every NPC needs **3 dialogue branches** matching the Mom-Test framing:

1. **One generic / useless branch:** Generic question → generic answer → 0 loyalty signal
2. **One specific / useful branch:** Specific question → useful past-behavior answer → +0.4 loyalty signal
3. **One specific / gold branch:** Specific question + future-behavior probe → gold answer → full loyalty signal + 3x revenue multiplier armed

For each branch: write the player's question (12-25 words), the NPC's response (15-50 words), the signal-quality classification, and revealedPreferences if gold.

**Cultural authenticity rules:**

- Any NPC speaking isiZulu / isiXhosa / Sesotho / Afrikaans / tsotsitaal must be reviewed by a native speaker before ship
- Code-switching is realistic (NPCs mix English with home language) — preserve this; don't sanitize
- Avoid stereotype lines ("eish all the time, township brother!"). Specific lived-detail beats generic SA-flavored copy
- The SA-cultural-advisor for v1 is TBD; budget R5,000-10,000 for a 4-6 hour review pass once dialogue is drafted

---

## Production timeline

| Phase | Days | Output |
|---|---|---|
| **Author 25 NPCs** (5 Soweto + 15 Khayelitsha + 5 drifters) | 2 days founder-time | Drafted in `Config/NPCs.luau` extension |
| **Cultural-advisor review** (4-hour pass) | 1 day cultural-advisor | Edits + flags + cultural reframes |
| **Author 25 more NPCs** (15 Mamelodi + 5 cross-district) | 2 days founder-time | Drafted |
| **Second cultural review** | 1 day cultural-advisor | Edits |
| **Voice-talent recording** (Voice123, ~50 NPC voice clips × 3-5 sec) | 5 days delivery | `assets/audio/npc-voice/` |
| **Localization** (translate top-tier dialogue lines into isiZulu/Sesotho/Afrikaans) | 3-5 days translator | Updated `shared/translations.lua` equivalent |

Total: ~2 weeks calendar with the cultural-advisor + voice-talent budget.

---

## Cost summary

| Item | Cost |
|---|---|
| Founder-time authoring (4 days) | R0 (you do it) |
| Cultural-advisor review (8h) | R5,000-10,000 |
| Voice-talent (50 clips × R200-400) | R10,000-20,000 |
| Localization (4 languages × ~200 strings) | R5,000-10,000 |
| **Total** | **R20,000-40,000** |

This is the single biggest content-budget line item for v1. It's also the
piece that, if done well, makes Founder Mode feel like a real SA cultural
product instead of "a Roblox tycoon with SA flavor."

Recommend starting with the founder-time authoring of NPCs 11-30 (no cash
spend), then reviewing playtest signal before committing the cultural-
advisor + voice-talent budget on NPCs 31-50.
