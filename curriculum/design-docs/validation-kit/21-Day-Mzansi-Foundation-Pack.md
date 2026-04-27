# 21-Day Plan — Mzansi Foundation Pack v1 (Tebex / FiveM)

**Decision locked 2026-04-27:** ship a bundled SA atmosphere pack as the 21-day product. Two distinctive products in one storefront launch: a load shedding mechanic + an amapiano radio pack. Both pure-code/pure-audio. No 3D-modeling freelance dependency. No calendar hostage.

**Product:** Mzansi Foundation Pack v1 — the SA atmosphere starter kit for FiveM RP servers.

**Sub-products (sold individually OR as bundle):**

| SKU | Product | Price | Ships day |
|---|---|---|---|
| 1 | **eKasi Load Shedding** (script) | $89 | 14 |
| 2 | **Mzansi Radio Pack** (amapiano + tsotsitaal DJ) | $49 | 21 |
| 3 | **Mzansi Foundation Pack** (bundle of 1+2) | $129 (save $9) | 21 |

**Revenue target:** 30-60 sales × $89-129 avg = **$2,670-7,740 in first 60 days.**

**Customer:** existing FiveM RP server owners — SA-themed servers (obvious market) PLUS "exotic immersion" servers globally that want a unique mechanic (load shedding has zero competitors anywhere on Tebex).

---

## Why this beats the vehicle pack

| Dimension | Vehicle Pack | Mzansi Foundation Pack |
|---|---|---|
| Days to ship | 30 (freelance-bound) | 21 (you control 100%) |
| 3D modeling required | Yes — 4 vehicles, 12 paints | No |
| Freelance dependency | Hard — pack ships only when artist delivers | None |
| Cultural moat | Vehicles exist on Tebex (~50+ packs); SA flavor differentiates | Zero direct competitors anywhere on Tebex |
| Revenue ceiling per pack | $89/license | $129/license bundle |
| Viral marketing potential | Medium (cool gusheshe screenshots) | High (load shedding mid-streamer-heist = SA Twitter goes brrr) |
| Pairs with future products | Yes (taxi job, tavern MLO) | Yes (vehicle pack v2 + tavern v3 + everything) |
| Calendar risk | High (artist late = sprint slips) | Low (Lua + audio = solo controllable) |

---

## SKU 1 — eKasi Load Shedding (Days 1-14)

### What it is

A Lua + UI script that simulates Eskom-style scheduled blackouts inside any FiveM server. SA RP servers feel real; non-SA RP servers get an exotic immersion feature no one else has.

### Mechanics

- **Schedule engine:** Server admin configures weekly load-shedding stages (1-8) per day per time slot. UI exposes the calendar both server-side (admin panel) and client-side (player phone notification).
- **Blackout effect:** When a stage hits, server-side broadcasts a `light_off` event. Streetlights, building exterior lights, and certain interior fixtures dim. Ambient audio fades. Generators kick in at properties that own one (item).
- **Inverter / generator items:** Players can buy an inverter ($800 in-game) or generator ($2500 in-game) from a hardware-store ped. While load shedding is active, properties with these items keep their lights AND keep perishable inventory fresh.
- **Inventory decay:** Properties with fridges that go offline = perishable items (configurable list: dairy, meat, beer, ice cream) lose value or rot at a configurable rate. Hits shop owners hard. Forces buy-an-inverter decisions.
- **NPC reactions:** When stage hits, nearby NPCs play panic animations and shout configurable lines (default: "Eishhh!", "Awe, ke 'Eskom' apha futhi!"). Default lines are en-ZA; tsotsitaal lines included as alternates; multilingual config-table support for server admins to add lines in isiZulu, Sesotho, Afrikaans.
- **Phone notification:** When a stage is about to hit (5-min warning), every online player gets a phone notification: "Stage 4 starts in 5 min. Your fridge will go off." Admin-configurable.
- **Schedule UI panel:** A read-only calendar inside the player phone or pause menu showing today's and tomorrow's scheduled stages.

### What ships in v1

Files (~12 Lua files + 1 NUI HTML + ~5 audio assets):

```
ekasi-loadshedding/
├── fxmanifest.lua
├── config.lua                  # admin-tweakable weights, stages, schedules
├── shared/
│   ├── schedule.lua            # stage calculation, time math
│   └── translations.lua        # localization-ready string tables
├── server/
│   ├── main.lua                # tick loop, stage broadcaster
│   ├── perishable.lua          # inventory decay logic
│   ├── inverter.lua            # ESX/QBCore item handling
│   └── events.lua              # outgoing events to clients
├── client/
│   ├── main.lua                # listens for stage events
│   ├── lights.lua              # darken streetlights, fixtures
│   ├── ambient.lua             # SFX (alarms, generator hum)
│   ├── npc.lua                 # NPC panic dialogue + animations
│   └── phone.lua               # phone notification
└── nui/
    ├── index.html              # schedule calendar UI
    ├── style.css
    └── app.js
```

### Day-by-day Week 1-2

**Day 1 (Mon):** Tebex seller account + Cfx dev account + private FiveM dev server stood up. ESX + QBCore both installed for compat testing. Brand decision locked: "Founder Mode Studios" or "eKasi Studios" (recommend Founder Mode Studios for brand alignment with the future Roblox game).

**Days 2-3 (Tue-Wed):** Spec the load shedding script in detail. Write `config.lua` first (you'll iterate this most). Stage 1-8 schedules baseline. Decide perishable item list. Decide inverter/generator economy.

**Day 4 (Thu):** Server-side: `schedule.lua` (time math, stage calculation), `main.lua` (the tick loop that fires stage events), basic logging. Test on private server: fake the time, verify stages fire correctly.

**Day 5 (Fri):** Server-side: `perishable.lua` (inventory decay), `inverter.lua` (item check), event broadcasting. Test: create a fridge with stock, fake load shedding, watch inventory decay.

**Days 6-7 (Sat-Sun):** Client-side: `lights.lua` (darken streetlights, building lights — uses RemoveBlip and World.SetExterior pattern), `ambient.lua` (generator hum, distant alarms), basic light-fade transitions. Test: player joins server, stage 4 hits, lights go off.

**Days 8-9 (Mon-Tue):** Client-side: `npc.lua` (NPC panic — TASK_PLAY_ANIM + speech callouts), `phone.lua` (5-min warning notification — works with qb-phone, lb-phone, gks-phone APIs).

**Days 10-11 (Wed-Thu):** NUI calendar panel. HTML + CSS + JS for the schedule UI. Renders the next 48 hours of stages. Localization-ready.

**Day 12 (Fri):** Localization: en-ZA strings done, plus tsotsitaal alternate lines. isiZulu, Sesotho, Afrikaans config-table stubs for server admins.

**Day 13 (Sat):** Polish + buyer-friendly README. Install instructions for ESX + QBCore. Config documentation. 60-second demo video showing stage 4 hitting a streamer's spaza.

**Day 14 (Sun):** **EARLY-ACCESS DROP.** DM 5-10 SA-themed FiveM RP server owners with a free license in exchange for honest review post-launch. Same pattern as the original vehicle plan.

---

## SKU 2 — Mzansi Radio Pack (Days 15-21)

### What it is

8-10 royalty-free amapiano tracks loaded as in-game FiveM radio frequencies. Pre-recorded tsotsitaal DJ voice intros between tracks. Plays in vehicles via the standard FiveM radio script + at custom locations (taverns, spazas, parties) via a small streamer Lua resource.

### Music licensing — the path

This is the highest-risk surface for music. Three legal sources:

1. **Pixabay amapiano** (CC0 / royalty-free, fully cleared for commercial use including resale embedded in products): pixabay.com/music/search/amapiano/. Quality is mixed but adequate.
2. **MusicHero.ai** (307 amapiano AI-generated tracks, licensed for commercial use including resale): musichero.ai/tag/Amapiano. AI-generated but defensible — explicitly licensed for distribution inside products.
3. **Mubert API** ($15/month subscription covers full commercial including resale embedded in shipped products): mubert.com.

**Recommended path:** Use 5 Pixabay tracks + 3-5 MusicHero.ai tracks. Total cost: $0-30 for licensing. Document each track's source + license in a `LICENSES.md` file shipped inside the resource. This is your audit trail if anyone questions it.

**Do NOT use:** YouTube-ripped amapiano, Spotify-ripped tracks, "popular SA artist" tracks without explicit written permission. The legal exposure on a Tebex product is real and asymmetric.

**Stretch (v2 of radio pack):** commission an SA amapiano producer for 3-5 original tracks at R3,000-5,000 with full commercial rights assigned. Save for v2; not in this 21-day sprint.

### Tsotsitaal DJ intros

Record 8-12 short DJ voice clips ("Phakama Mzansi, this is your DJ on Founder Radio, sharp sharp"). Options:

- **Self-record** if the user has voice acting comfort. iPhone voice memo + iZotope cleanup. ~2 hours work.
- **Commission an SA voice actor** via Fiverr or Voice123. ~R500-1,500 for 12 clips. ~3-5 day delivery.
- **AI voice clone** — ElevenLabs has decent SA-English voices. ~$5 for the clips. Risk: AI voices in a cultural product are taste-sensitive.

Recommend: self-record OR commission Voice123. AI voice for a CULTURAL product undercuts authenticity.

### What ships in v1

```
mzansi-radio/
├── fxmanifest.lua
├── config.lua                  # frequency assignments, station name
├── client/
│   ├── radio.lua               # vehicle radio integration
│   └── jukebox.lua             # location-based playback (tavern, spaza)
├── audio/
│   ├── track-01-pixabay-amapiano-001.ogg
│   ├── track-02-musichero-amapiano-002.ogg
│   ├── ...
│   ├── dj-intro-01.ogg
│   ├── dj-intro-02.ogg
│   └── ...
└── LICENSES.md                 # explicit licensing audit trail
```

### Day-by-day Week 3

**Day 15 (Mon):** Source + audition + license-clear 8-10 tracks. Pixabay scrape + MusicHero.ai pick. Document each in LICENSES.md.

**Day 16 (Tue):** Record or commission 12 tsotsitaal DJ intro clips. Drop into a `dj-intro-XX.ogg` set.

**Day 17 (Wed):** Audio normalization + format conversion (FiveM uses .ogg / .wav at specific sample rates). Test in private dev server's vehicle radio.

**Day 18 (Thu):** Build `client/radio.lua` (frequency hook into FiveM's stock radio), `client/jukebox.lua` (location-based playback for tavern/spaza). Config for which frequencies map to which playlist.

**Day 19 (Fri):** Tebex storefront final setup — three SKUs (Load Shedding alone, Radio Pack alone, Mzansi Foundation bundle). Pricing locked. Bundle math obvious to buyer.

**Day 20 (Sat):** Marketing drop:
- YouTube: 90-second showcase combining Load Shedding + Radio Pack ("when stage 4 hits and your gusheshe is at the spaza, the amapiano keeps playing through the inverter")
- TikTok vertical: 30s cut of the same moment
- Reddit r/FiveM: "[Release] Mzansi Foundation Pack — load shedding + amapiano radio for FiveM"
- SA gaming Twitter + IG: tagged drops, 3 servers tagged
- DM the early-access servers: "live now, post your honest review"

**Day 21 (Sun):** **PUBLIC LAUNCH.** Tebex live. Cfx Marketplace submitted (review takes 1-2 weeks; fine, Tebex sells in parallel).

---

## Days 22-30 — buffer + iterate + plan v2

**Days 22-25:** Customer support, server-owner integration help, bug fixes, FAQ.

**Days 26-28:** Use buyer feedback to plan v2. Probable v2 candidates:

| v2 candidate | Days to ship | Why |
|---|---|---|
| **Vehicle Pack** (the original plan) | 30-35 | Pairs PERFECTLY with Foundation Pack — gusheshe at the spaza when load shedding hits |
| **Township Tavern (Shebeen) MLO** | 28-42 | The radio pack + tavern = social hub product line |
| **Spaza Shop Interior MLO** | 21-28 | Pairs with load shedding (perishable inventory has somewhere to live) |
| **Taxi Rank Job Script** | 21 | Pure code; pairs with vehicles when those ship |

**Days 29-30:** End-of-month review. Track:

| Metric | Target | Floor |
|---|---|---|
| Tebex sales | 30+ | 10 (wedge proven) |
| Bundle vs single ratio | 60%+ bundle | 30%+ bundle |
| Reviews | 8+, 4.5+ star avg | 5+, 4.0+ star avg |
| Active SA RP servers using it | 5+ visible | 2+ |
| TikTok/YouTube combined views | 5,000+ | 1,000 |
| Clear v2 spec emerged from feedback | yes | a list of 3 candidates |

---

## Setup checklist (Day 1)

- [ ] Tebex seller account verified (Stripe payout)
- [ ] Cfx developer account
- [ ] Private FiveM dev server (DigitalOcean / Hetzner $12/month)
- [ ] ESX-Legacy + qbcore-framework installed
- [ ] Brand name locked (recommend: **Founder Mode Studios** for cross-brand alignment with the future Roblox game)
- [ ] YouTube channel + TikTok account at matching handle
- [ ] Tebex storefront URL reserved
- [ ] LICENSES.md template ready for the audio audit trail
- [ ] Voice123 / Fiverr account if commissioning DJ intros

## Roblox audience-warming track (unchanged from prior plan)

Same 15% time allocation:
- Week 1: Send Roblox stokvel policy email (file 05) — fire and forget
- Week 1-2: Begin DevEx + W-8BEN paperwork (file 06) — background
- Week 2-3: Drop the concept video on TikTok (files 01, 03)
- Week 3: Publish placeholder Roblox page (file 04)
- Week 3: Run 3 kid interviews (file 02) — directional research, not gating

---

## Why this is genuinely better than the vehicle plan

1. **You're not hostage to a freelancer.** Every day of progress is in your hands.
2. **The cultural moat is higher.** Load shedding is unmistakably SA. Anyone in the world can model a BMW.
3. **Bundle pricing > single product pricing.** $129 average ticket beats $89 from day 1.
4. **Storefront identity from day 1.** Two products in one launch = "they're a real shop with a vision," not "they sell one car pack."
5. **Faster to first revenue.** 21 days vs 30. Two weeks of cash flow earlier.
6. **Lower legal risk on assets.** Pure royalty-free audio + your own Lua code. No real-vehicle-IP gray area.
7. **Compounds with the future vehicle pack better.** When the vehicle pack ships in months 2-3 as v2, the gusheshe spinning at the spaza when load shedding hits IS the differentiated moment. The Foundation Pack creates the world; vehicles inhabit it.

## Day 1 — start here

1. Tebex seller account → tebex.io/auth/register
2. Cfx developer account → forum.cfx.re
3. DigitalOcean droplet → install Linux + FiveM server + ESX/QBCore (~2 hours)
4. Decide brand name: **Founder Mode Studios** (recommended for cross-brand) or **eKasi Studios** (kasi-coded)
5. Create `ekasi-loadshedding/` folder + `fxmanifest.lua` skeleton
6. Pull up Claude and ask it to write `shared/schedule.lua` — the stage-time-math module is the foundation of everything

By end of Day 1: dev server running, brand picked, repo created, first Lua file in. Day 14 you ship Load Shedding. Day 21 you ship the bundle.
