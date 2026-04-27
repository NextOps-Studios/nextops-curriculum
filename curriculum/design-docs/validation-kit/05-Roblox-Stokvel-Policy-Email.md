# 05 — Roblox Stokvel Policy Inquiry Email

**Goal:** get a written response from Roblox Developer Relations on whether the stokvel mechanic clears their content moderation policy. The eng review locked this as a gate before any stokvel ships.

**Why it matters:** Roblox has de-listed games for "implied gambling" (rotating-payout mechanics, lotteries, real-money currency simulation). Even a fixed-rotation single-player NPC stokvel sits adjacent to those flags. A written clarification protects you from a launch-week de-listing.

**Lead time:** 2-6 weeks for a substantive response. Send it in week 1 so the response window runs in parallel with everything else.

---

## Where to send it

**Primary:** the Roblox Developer Relations / Trust & Safety contact form at:
- `devforum.roblox.com` → create a thread in the "Help and Feedback → Feature Discussion" or "Public Roads" category, AND
- Direct email: `developerrelations@roblox.com` (verify the current address before sending — Roblox occasionally rotates these). If the email bounces, fall back to opening a ticket via the Roblox Developer Hub support form.

**Tone:** developer-to-developer, not founder-pitching. Roblox DevRel sees thousands of pitches per week. They respond best to specific, narrow, technical questions with clear non-gambling framing already in place.

**Subject line:**

```
Policy clarification: rotating-savings mechanic ("stokvel") — fixed pre-set rotation, no randomness
```

---

## The email (paste verbatim, swap [placeholders])

```
Hi Roblox Developer Relations,

I'm building a tycoon game called Founder Mode: Mzansi — a township informal-economy simulator for Roblox. Place ID: [your placeId]. I'm reaching out for a policy clarification before I implement a specific cultural mechanic.

The mechanic is called a "stokvel." It's a real-world South African and pan-African savings-club tradition: a fixed group of people contribute a set amount each month, and each month one member receives the full pot, in a pre-arranged rotation order. Every member receives exactly one payout per cycle. There is no randomness, no luck, no betting, and no real-money currency.

In Founder Mode, the player's character joins or starts a stokvel with NPC members. It functions as a savings device for big in-game purchases (commercial fridge, minibus, salon expansion).

I want to make sure this mechanic is clearly distinguishable from any "implied gambling" content under Roblox community standards. To that end, here is the explicit non-gambling design proof I plan to ship:

1. ROTATION ORDER IS FIXED AND PRE-SET. When the player joins a stokvel, the rotation order is determined at join time and visible immediately on a calendar UI. Every payout date is shown for every member. There is no surprise, no "spin," no random selection event.

2. NO LUCK OR WHEEL FRAMING. The UI is exclusively a calendar. There is no spinning wheel, no roulette visual, no "your turn was randomly drawn" copy. The player sees their payout month from day one.

3. NO REAL-MONEY CURRENCY SIMULATION. Contributions are paid in the in-game currency only ("R" / kasi cash). The in-game currency is non-transferable between players, has no Robux conversion path, and is not redeemable.

4. EVERY MEMBER RECEIVES EXACTLY ONE PAYOUT PER CYCLE. No member can win more than another. The total contributions equal the total payouts. There is no house edge, no profit to any party other than the rotation participants.

5. SKIP-A-CONTRIBUTION PENALTIES ARE TRANSPARENT. If a member misses a contribution, the consequences are stated upfront on the join UI (reputation penalty, possible removal). No hidden mechanics.

6. NO SOLICITATION OR REAL-WORLD MONEY OUTSIDE ROBLOX. The stokvel never solicits real-world payments outside Roblox's ecosystem. No external links, no Discord-monetization tie-ins.

For v1, the stokvel is single-player only — the 9 other members are NPCs. Multiplayer player-to-player stokvels are gated behind this policy clarification and would only ship if explicitly cleared.

The mechanic has cultural and educational significance: stokvels (and their pan-African equivalents — esusu in Nigeria, susu in Ghana, chama in Kenya, ROSCAs globally) are a foundational financial-literacy concept and one of the few pre-banking financial structures that still operates at scale. I'm building this game so kids in SA and across Africa can grow up seeing their grandmothers' financial wisdom represented inside Roblox.

My questions:

A) Does the design above clear Roblox's "no implied gambling" guideline?
B) Are there specific UI patterns or copy you'd recommend I AVOID even given the design above?
C) Is there a written policy document you can point me to that addresses culturally-rooted savings-club mechanics, or is this novel territory for the platform?
D) If single-player is cleared, is there a path for multiplayer stokvels (real player-to-player) to be cleared in a later version, with what additional safeguards?

I'm happy to send a 60-second design walkthrough video, share Studio screenshots of the calendar UI, or get on a call. I want to design this responsibly from day one, not retrofit after launch.

Thank you for your time.

Best,
[Your name]
[Your email]
[Your TikTok handle]
[Your Roblox username + game URL]
```

---

## What to do with the response

When Roblox DevRel responds, log it to:

`~/Desktop/Founder-Mode-Validation-Kit/roblox-policy-response-2026-MM-DD.md`

Capture:
- Date received
- Verbatim response (full text)
- Cleared / cleared with conditions / declined
- If cleared with conditions: enumerate the conditions, add each to the design doc as a constraint
- If declined: cut the stokvel mechanic entirely. Replace with a "savings goal" mechanic (player sets a target amount, NPCs cheer them on as they accumulate, no rotation). Update design doc.

**If no response after 4 weeks:**
- Resend with subject line prefix: `[follow-up]`
- Post a public thread on devforum.roblox.com with the same content (transparency increases response rate)
- DO NOT ship stokvel speculatively. The risk of de-listing post-launch is far worse than waiting.

---

## Pitfalls

- **Don't conflate "stokvel" with "lottery" anywhere in your copy or UI.** They are categorically different (rotation is fixed, payouts are equal). Casual language can poison the framing — train yourself to say "savings rotation" if "stokvel" requires more explanation in any future material.
- **Don't ship stokvel before getting the response.** Even if you're 99% sure it'll clear, the de-listing risk is asymmetric — small upside to shipping early, catastrophic downside if Roblox pulls the game.
- **Don't overstate the cultural importance to manipulate the reviewer.** State it once, plainly, and let the design proof carry the policy argument. Cultural appeals to game-policy reviewers fall flat; technical clarity wins.
- **Don't pitch the broader game in the same email.** This is a narrow policy question. Pitching Founder Mode as "the next big SA Roblox game" widens the scope and slows the response. Keep it surgical.
