# 30-Day Plan — Mzansi Vehicle Pack v1 (Tebex / FiveM)

**Decision locked 2026-04-27:** ship a Tebex Asset Pack first as the 30-day product. Founder Mode Roblox v1 begins after the Tebex pack ships, funded partially by Tebex revenue and de-risked by 30 days of audience and pipeline learning.

**Product:** Mzansi Vehicle Pack v1 — 4 SA-iconic vehicles, 3 paint jobs each, ESX + QBCore compatible, sold on Tebex.

**Revenue target:** $1,500-5,000 in 90 days from this single pack.

**Customer:** existing FiveM RP server owners running SA-themed or aspirationally-localized servers (Mzanzi Reborn, MLG Crisis, SA LIFE, plus diaspora servers).

---

## What ships

| # | Vehicle | Why this one | Pricing tier |
|---|---|---|---|
| 1 | **BMW 325is "Gusheshe"** | The hero. SA spinning culture's defining vehicle. Cult YouTube/TikTok audience. Selling this one alone justifies the pack. | Hero ($) |
| 2 | **Toyota Quantum minibus** | The taxi. Universal SA recognition. Useful for any RP server simulating SA streets. | Hero ($) |
| 3 | **VW Polo** | The young-hustler car. Almost every kasi street has one. Daily-driver authenticity. | Standard ($$) |
| 4 | **Township bakkie (Toyota Hilux / Nissan NP200 style)** | Workhorse. Hawkers, scrapyards, deliveries. Functional vs. flashy — covers the working-class angle. | Standard ($$) |

Each vehicle ships with 3 paint jobs (stock, kasi-loud, faded-rusty). Total: 4 vehicles × 3 paints = 12 visual SKUs in one pack.

**Pack price:** $89 USD per server license (Tebex). Bundle discount: pack + future "Sound Pack" + future "Map MLO" → $199 bundle.

**No real-world brand logos.** All vehicles are "inspired by" — no BMW, Toyota, or VW logos that could trigger a takedown. Custom emblems and kasi-coded visual language (hand-painted slogans, stickers, modded body kits).

---

## 30-day calendar

### Week 1 — Asset commissioning + Tebex setup (Days 1-7)

**Day 1 (Monday):**
- Decide: commission a freelance 3D artist (recommended — saves 2 weeks) OR self-model in Blender.
- If commissioning: post a job on Fiverr ("FiveM YFT vehicle conversion + custom textures") AND in two SA 3D-artist Discords. Budget R4,000-8,000 for 4 vehicles. Lead time: 7-12 days for a competent freelancer.
- Reference materials: send the artist 10 photos of each real vehicle (BMW 325is gusheshe, Quantum, Polo, bakkie) with kasi-modded examples. Critical: the kasi mods (oversized tail lamps, custom rims, hand-painted slogans) are the differentiator.
- Open a Tebex seller account: tebex.io/auth/register. Set up Stripe payout. Verify identity.

**Day 2 (Tuesday):**
- Open a Cfx (Rockstar) developer account: forum.cfx.re. Required for Cfx Marketplace listing.
- Spin up a private FiveM development server. DigitalOcean droplet (2GB RAM, $12/month) or Hetzner CCX13 (cheaper). Install ESX-Legacy or qbcore-framework as a base.
- Create Tebex storefront. Brand name: "eKasi Studios" or "Mzansi Mods" or whatever you settle on. Match the brand to your future Founder Mode Roblox brand (could be the same — "Founder Mode Studios").

**Days 3-5 (Wed-Fri):**
- While freelance artist works on the vehicles, you build the Lua/integration layer in parallel.
- Write `mzansi_vehicles/__resource.lua` (or `fxmanifest.lua` for new format).
- Write a config file `mzansi_vehicles/config.lua` exposing: spawn points, vehicle spawn rates, dealer NPC location, price tiers, ESX/QBCore mode flag.
- Write `mzansi_vehicles/server.lua` for vehicle purchase / spawn / persistence. ESX integration uses xPlayer.removeMoney() and xPlayer.addAccountMoney(). QBCore integration uses Player.Functions.RemoveMoney() and Player.Functions.AddItem() patterns.
- Write `mzansi_vehicles/client.lua` for the dealer interaction UI (NUI HTML/CSS or QBCore's drawText 3D).
- Claude can write all of this in a few hours. The work is integration testing, not authoring.

**Days 6-7 (Sat-Sun):**
- Polish: write README.md (install instructions, framework compatibility, config options), 2-3 demo screenshots (the dealer scene + the vehicle in motion + the spinning arena).
- Set up a YouTube channel. Record 1-min "vehicle showcase" demo using the freelance assets when they arrive (placeholder if not yet).

### Week 2 — Asset integration + early access (Days 8-14)

**Day 8 (Monday):** First freelance vehicle drop expected. Test in Studio + private FiveM server. Verify YFT format, hands-on-wheel positioning, engine sound, paint slots, headlight LOD.

**Days 9-11 (Tue-Thu):** Iterate freelance feedback. Fix paint slot bugs, weight, handling.meta tuning (gusheshe needs RWD-spinny handling, bakkie needs slow-truck handling). Add the 3 paint jobs per vehicle.

**Days 12-13 (Fri-Sat):** All 4 vehicles in. Integration test on private FiveM server with both ESX and QBCore. Verify: dealer purchase flow, spawn at dealer, vehicle persists across server restart, paint job selection works, no client crashes.

**Day 14 (Sun):** **EARLY-ACCESS DROP.** DM 5-10 SA-themed FiveM RP server owners (Mzanzi Reborn, MLG Crisis, SA LIFE, plus 2-3 diaspora servers). Offer: free license in exchange for honest review on Tebex post-launch. This is the audit's review-velocity strategy.

### Week 3 — Public launch + audience build (Days 15-21)

**Day 15 (Monday):** Publish to Tebex. Public listing live. Set price $89.
- Tebex storefront: full description, 5 screenshots, demo video, install README, comparison table vs. generic drift packs.
- Cfx Marketplace: separate listing with same content. Submission review takes 1-2 weeks; that's fine, Tebex sells in parallel.

**Day 16-17 (Tue-Wed):** Marketing drop:
- YouTube: 60-second showcase video.
- TikTok: vertical cut of the spinning gusheshe with amapiano backing track, hashtag #fivemsa #spinning #gusheshe #mzansi.
- Reddit: r/FiveM "[Release] Mzansi Vehicle Pack — 4 SA-iconic vehicles, ESX/QBCore, $89."
- SA gaming Twitter: tag MLGC Prime, Unity RP ZA, SA gaming influencers.
- DM the early-access servers: "live now, post your honest review on Tebex."

**Day 18-21 (Thu-Sun):** Reply to every comment, every DM, every review. The first 5 reviews determine the conversion rate for the next 1,000 store-page views.

### Week 4 — Iterate + plan v2 (Days 22-30)

**Days 22-25 (Mon-Thu):** Customer support. Bug fixes. Server-owner integration help (each install differs). Build a FAQ.

**Days 26-28 (Fri-Sun):** Use the comment + review patterns to plan v2 (next pack). Likely candidates surfaced from buyer feedback:
- "Township Map MLO" — Soweto-style street block, high-demand companion product
- "Mzansi Sound Pack" — amapiano radio stations, hadeda ambient, taxi hooters
- "Diski Streets Pack" — brick-goal soccer mod for FiveM
- "Spinning Arena MLO" — the actual arena map, paired with the vehicle pack

**Days 29-30 (Mon-Tue):** End-of-month review.
- How many sales? Target: 15-30 sales × $89 = $1,335-2,670 in first month.
- How many reviews? Target: 5+ reviews, 4.5+ star avg.
- What did buyers ask for that you didn't have? That IS the v2 spec.
- Decide: ship a v1.5 patch (free for buyers, fixes top complaints), then start planning v2 OR roll directly to Founder Mode Roblox v1 build.

---

## Reframing the existing Roblox validation kit

The 6-file validation kit on your Desktop was scoped for Founder Mode Roblox v1 build readiness. With the Tebex-first decision, those gates are NOT abandoned — they're reframed:

| Validation kit file | Reframed role under Tebex-first plan | Priority |
|---|---|---|
| `01-Concept-Video-Storyboard.md` | Still ship the TikTok video. But it's now an **audience-warming asset for the future Roblox v1 launch**, not a validation gate. Posts on TikTok during weeks 3-4 of the Tebex sprint to start building the Founder Mode Roblox audience while Tebex runs. | Medium (week 3) |
| `02-Kid-Interview-Kit.md` | Still do the 3 kid interviews. Now they're **directional research for Founder Mode Roblox v1** which begins in month 2. No build gating on this. | Low (month 2) |
| `03-TikTok-Post-Variants.md` | Use Variant A in week 3 of the Tebex sprint to seed Founder Mode Roblox audience. The Tebex pack gets its own TikTok content (gusheshe spinning footage). Two parallel channels. | Medium (week 3) |
| `04-Roblox-Placeholder-Page-Copy.md` | Publish the empty Roblox page in week 3. Accumulates favorites passively while Tebex pack ships. | Low-Medium (week 3) |
| `05-Roblox-Stokvel-Policy-Email.md` | Send in week 1. Lead time runs in parallel; response arrives sometime in months 2-3 when Founder Mode Roblox build actually needs the answer. | Low (week 1, fire-and-forget) |
| `06-DevEx-W8BEN-Checklist.md` | Background admin track. Multi-week processing. Start now so it's done by the time Founder Mode Roblox earns Robux. Tebex revenue does NOT need DevEx (Tebex pays separately). | Low (background) |

**Time allocation across 30 days:**
- 80% Tebex Asset Pack focused work (~24-28 hours/week)
- 15% Roblox audience-warming (TikTok video drop, placeholder Roblox page, 3 kid interviews) (~4-6 hours/week)
- 5% admin (Roblox stokvel email, DevEx paperwork) (~1-2 hours/week)

---

## What the May 11 check-in agent will now ask

The scheduled agent (`trig_01FpRNb6u5AGCM7vqiEWPbDB`) will fire on May 11, ~14 days into the Tebex sprint. It will still ask the original 5 questions but the answers map differently:

1. **Kid interviews:** "Did you do them? They're now directional research, not gating. Insights inform Founder Mode Roblox v1 spec."
2. **Roblox stokvel policy email:** "Sent? Any response yet? Still gates the Roblox stokvel mechanic when that build begins."
3. **DevEx + W-8BEN:** "Started? Background paperwork, lower priority but lead time matters."
4. **Roblox-native demand signals:** "TikTok plays / Roblox favorites since week 3 drop? Audience size for the future Roblox launch."
5. **Proceed or pivot:** Now reframed: "Tebex pack on track to ship by day 30? Any reviews coming in? Real money flowing? If yes, Founder Mode Roblox v1 starts day 31. If Tebex pack is delayed or zero traction, reassess."

You'll likely answer the May 11 agent with: "Tebex pack mid-build, freelance assets in, integration testing, public launch day 15. Audience-warming kit dropped in week 3."

---

## Required setup checklist (Day 1)

- [ ] Tebex seller account (tebex.io/auth/register) — Stripe payout verified
- [ ] Cfx developer account (forum.cfx.re)
- [ ] Private FiveM dev server (DigitalOcean / Hetzner ~$12/month)
- [ ] ESX-Legacy + qbcore-framework installed on dev server
- [ ] Brand name decision (eKasi Studios / Mzansi Mods / Founder Mode Studios — recommend the last for brand alignment)
- [ ] Freelance 3D artist hired OR Blender modeling decision made
- [ ] Reference photo pack assembled (10 photos × 4 vehicles = 40 images)
- [ ] Tebex storefront URL reserved
- [ ] YouTube channel created (matches brand)
- [ ] Stripe USD account confirmed (or Wise USD virtual account from validation kit file 06)

## Risks and mitigations

| Risk | Likelihood | Mitigation |
|---|---|---|
| Freelance artist delivers late or low-quality | Medium | Hire from Fiverr Pro tier (vetted), set milestones (50% on first vehicle, balance on completion), have a backup artist on standby |
| Tebex storefront review rejects the listing (asset quality, IP concerns) | Low | All vehicles "inspired by" — no real logos. Tebex is generally founder-friendly; rejections are rare for clean assets |
| Cfx Marketplace review takes 4+ weeks | Medium | Sell on Tebex in parallel; Cfx is bonus reach not gating |
| Zero sales in week 1 of public launch | Medium | Early-access free-license-for-review strategy creates first 5 reviews. Without those, conversion is ~0%. Don't skip Day 14 outreach. |
| Server-owner DMs ignored | Medium-High | Personal warm intros via SA gaming Discord communities. Cold DMs convert at <5%; warm intros via Discord member-of-server convert at 20-30%. |
| ESX vs. QBCore framework drift | Low | Both frameworks are mature; Claude knows both. Test on both private dev servers from Day 12. |
| You hate FiveM Lua and abandon mid-sprint | Real | Trust the sprint. 30 days of focused FiveM work funds 10 months of Founder Mode Roblox. Discipline through it. |

---

## What success looks like at Day 30

- Mzansi Vehicle Pack v1 published on Tebex + Cfx Marketplace
- 5+ honest reviews (target 4.5+ star avg)
- 15-30 sales × $89 = $1,335-2,670 first-month revenue
- ~3-5 SA RP servers actively using the pack (community proof)
- 2 TikTok / YouTube demo videos with combined ~5,000 views
- A clear v2 spec emerged from buyer feedback (Township Map MLO, Sound Pack, Diski Pack — pick one)
- Founder Mode Roblox audience-warming complete: TikTok video posted, placeholder Roblox page live, ~50-200 Roblox favorites accumulating, ~500-2,000 TikTok plays, kid interviews done

**On Day 31:** decision to make.
- (a) Roll into Founder Mode Roblox v1 build (10-month timeline as planned, now funded by Tebex revenue and de-risked by 30 days of pipeline experience)
- (b) Ship a Tebex pack v2 first (Township Map MLO or Sound Pack) — compounds the storefront, delays Roblox by another 30 days
- (c) Both in parallel — only viable if Tebex revenue covers a part-time freelance helper or if you're at 35-40 hours/week of focused dev capacity

The May 11 check-in agent (firing day 14) will help calibrate which of these makes sense at that point.
