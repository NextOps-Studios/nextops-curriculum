---
concept: Customer Discovery
pillar: 3
status: approved
created: 2026-04-28
agent_run_id: human-seed-001
sources_verified: yes
---

# Customer Discovery

## What it is (90-second version)

Customer discovery is the act of talking to real customers BEFORE you build a product, to find out what they actually want, what they actually struggle with, and what they actually pay for. It is the opposite of "build it and they will come."

Steve Blank, the entrepreneur who codified this idea in *The Four Steps to the Epiphany* (2005) and *The Startup Owner's Manual* (2012), summarized it as: **"Get out of the building."** The startup that wins is the one whose founder spent the most time inside their customers' lives before writing a line of code.

The mistake every first-time founder makes: assume customers want what the founder thinks is cool. The mistake every second-time founder catches: customers don't tell you what they want; they show you what they're already doing. Watch the doing.

## Why it matters

Without customer discovery, you build products nobody wants. With customer discovery, you build products customers were already trying to build for themselves — and you get there faster. The cost of being wrong about what customers want, *after* you've built the product, is months of wasted code and dead capital. The cost of being wrong *during* customer discovery is one awkward conversation.

The sharper claim: every business decision downstream of "what does the customer want?" is based on assumptions until you talk to the customer. Pricing assumptions, packaging assumptions, marketing-channel assumptions, even the choice of who to hire next — all of them collapse if the foundational customer-want assumption is wrong.

In SA + African contexts, customer discovery has a sharper edge: the customer is often someone the founder thinks they understand because the founder grew up adjacent to them. "I know spaza customers because my gogo ran one" is not customer discovery — it is the founder's nostalgia. The actual spaza customer in 2026 has different behaviors than the spaza customer in 2006: they buy airtime more than bread, they read the prices off a price-comparison TikTok, they expect to pay via a QR code. The founder who skips discovery because they "already know" ships a 2006 spaza in 2026.

## Real-world examples

**Airbnb's first 100 customers.** Brian Chesky and Joe Gebbia famously flew to New York and *physically photographed every host's apartment themselves*. They learned that hosts had no idea how to take attractive listing photos — and the lack of attractive photos was killing bookings. They didn't survey hosts; they sat in hosts' apartments. The professional-photography service became one of Airbnb's biggest unlocks. (Source: *Founders at Work*, Jessica Livingston, 2007.)

**Yoco's 2015 SA founder discovery.** Carl Wazen and Katlego Maphai (Yoco co-founders) spent the first six months interviewing small-business owners across SA before writing payment-processing code. They discovered that the gap was not "no card machines exist" but "card machines exist but cost R3,000 upfront and require a year-long Vodacom contract." They built a R599 device with no contract. By 2024, Yoco processed >R50bn/year. (Source: Yoco's own founder posts on LinkedIn; verified against *TechCabal* coverage 2018-2024.)

**Failure case: Quibi's $1.75B mobile-only video service.** Quibi raised $1.75bn from Disney, Alibaba, JP Morgan, and others on the thesis that mobile-only short-form premium video would succeed. They never ran customer discovery interviews with the target demographic (Gen Z + millennial commuters). They hired Hollywood execs and built a beautiful product. The pandemic ended commuting, and even before that, the target audience preferred TikTok's free format over Quibi's premium. Quibi shut down 6 months after launch and returned what it could to investors. (Source: *Wall Street Journal*, "Inside the Spectacular Failure of Quibi," 2020-10.)

The lesson the failure case teaches: customer discovery is non-negotiable even when you have a billion dollars and a perfect-looking team. Quibi had everything except evidence that anyone wanted the product.

## In-game expression — Founder Mode mapping

This concept fires in v1 through the **NPC dialogue mechanic** in Founder Mode's spaza tycoon loop.

### The mechanic

When a customer NPC walks into the player's spaza, a "want bubble" appears above their head with a vague indicator. The player has two choices:

1. **Guess-stock:** Try to sell whatever's on the shelf. If the player's stock matches the NPC's actual want, the sale fires. If not, the NPC walks out unsatisfied. Revenue: 1x the product price.
2. **Talk-first:** Click the NPC and choose a dialogue branch. The NPC reveals specific past-behavior details ("I bought bread Tuesday and Friday last week. Today I just want airtime"). With this information, the player stocks correctly. Revenue: 3x the product price (the customer becomes a regular).

### Why it lands the lesson

The 3x multiplier is the curriculum mechanic. Players who guess-stock survive but barely; players who talk-first thrive. Within 20 minutes of play, the talk-first behavior becomes the default not because a tutorial said so but because it works.

Repeat customers the player has talked to enter the player's `namedRegulars` profile data (see `nextops-founder-mode-roblox/src/ReplicatedStorage/Modules/Types.luau`). Their loyalty + last-purchase + preferred-products are all persisted. This is the substrate that lets v1.1 ship the loyalty meter UI and v1.2 ship the customer-portrait gallery.

### Specific NPC dialogue lines (the Mom Test framing)

**Bad (generic question yields generic answer):**
- Player: "What do you want?"
- NPC: "I dunno, what you got?"
- → Useless. Player is no smarter.

**Good (specific past-behavior question yields useful answer):**
- Player: "When was the last time you bought from a spaza?"
- NPC: "Friday last week. I got bread, milk, and a Grand-Pa headache powder. The bread had gone stale by Saturday so I haven't been back."
- → Gold. Player learns: stock fresh bread, the customer values quality over price, Grand-Pa is a regular need.

**Better (specific behavior + future-behavior probe):**
- Player: "If I had R50 of fresh bread waiting tomorrow morning, would you come back?"
- NPC: "Yebo, I'd come every morning before work. The kids need lunch sandwiches."
- → Even better. Player learns: there's a daily-bread subscription opportunity hiding in this customer.

The dialogue trees in `nextops-founder-mode-roblox/src/ReplicatedStorage/Config/NpcDialogue.lua` are designed against Rob Fitzpatrick's *The Mom Test* (2013) — generic questions get generic answers; specific past-behavior questions get useful answers. Players who learn to ask the second kind win the game.

### Cross-link

This concept compounds with:
- **Problem-Solution Fit** (per-district stocking): customer discovery within ONE district reveals district-specific preferences.
- **The Day Report** (build-measure-learn): the data from talk-first conversations populates "asked for, not stocked" rows in the next day's report.
- **Stokvel** (capital pooling): regulars become stokvel candidates; talking to customers is also recruiting future co-investors.

## Real-world bridge

A player who has internalized "talk to your customers" inside the game can apply it the same week:

- **Real-world challenge unlock:** "Visit a real spaza near you. Ask the owner: 'What's the one product you wish you stocked but don't?' Write down the verbatim answer. Submit on the Founder Mode TikTok with #customerdiscovery for a free in-game cosmetic."
- **Career application:** Anyone interviewing for product/sales/marketing roles is being assessed on customer-discovery instinct without knowing it. Players who've done the in-game version can articulate what they did and why in a job interview.
- **Side-project application:** A 14-year-old who wants to launch a t-shirt brand has been trained to text 5 friends and ask "what's the last shirt you bought and why?" before designing anything. This is the lesson.

## Pedagogy notes (for the design team)

- The curriculum's eight rules in `07-pedagogy-design-rules.md` apply: never use the words "customer discovery," "Mom Test," or "Steve Blank" inside the game. The mechanic carries the lesson; the player learns by doing.
- The 3x revenue multiplier on talk-first interactions IS the curriculum. Reduce it and the lesson weakens. Eliminate it and the lesson dies.
- Crucially, the player must lose money the first time they guess-stock so the talk-first lesson registers viscerally. Never make guess-stock free.
- The brand-partnership pitch deck for FNB / Capitec / Yoco can absolutely cite Steve Blank, *The Mom Test*, and the customer-discovery literature. That credibility lives at the partnership layer, not the player layer.

## Open questions for human review

1. **Should v1 expose a "talk-first hint" tutorial?** Pure stealth pedagogy says no — players should discover talk-first themselves. But if D1 retention drops because guess-stocking players churn before discovering it, the right call may be a single subtle tutorial line from the gogo NPC. Decision pending playtest data.
2. **Where does the 3x multiplier live in code?** Currently planned for `Economy/init.luau` `onSellToCustomer` handler. Should it be config-tunable per district (richer districts = lower multiplier because customers shop fast)?
3. **Should the talk-first mechanic apply to v2 businesses (salon, taxi rank)?** The pedagogy is universal but each business has different customer-discovery shapes. Salon = "what's your usual hair routine?", Taxi = "where do you commute every weekday?". Spec these in v2 deep-dive.

## Sources

- Steve Blank, *The Four Steps to the Epiphany*, 2005 — [stanford.edu reading](https://www.stanford.edu/group/innovation/) (originally self-published; widely cited in tech ecosystem)
- Steve Blank + Bob Dorf, *The Startup Owner's Manual*, 2012 — [steveblank.com](https://steveblank.com/category/the-startup-owners-manual/)
- Rob Fitzpatrick, *The Mom Test*, 2013 — [momtestbook.com](https://www.momtestbook.com/)
- Jessica Livingston, *Founders at Work*, 2007 (Airbnb chapter)
- *Wall Street Journal*, "Inside the Spectacular Failure of Quibi," 2020-10
- Yoco founder posts on LinkedIn + *TechCabal* coverage 2018-2024 — verify when citing in pitch decks (avoid undated quotes)

---

This concept was hand-written as a seed exemplar for the Curriculum Agent. The agent's daily fires (starting tomorrow) will follow this template structure. Human edits welcome — comment with `tighten` or `expand` to adjust before approving.
