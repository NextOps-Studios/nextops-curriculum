# First Roblox Studio Playtest — Step-by-Step Checklist

**Goal:** open the existing Founder Mode codebase in actual Roblox Studio
for the first time, run the project end-to-end, and log every bug/issue.
This is the highest-leverage 2-hour activity in the entire build.

**Why it matters:** the lint+build CI verifies the project COMPILES. It does
NOT verify behavior. Code that's CI-green can crash on every player join,
silently fail to fire any RemoteEvent, throw runtime type errors, or just
look like an empty baseplate. Until you actually press Play, you don't know
what you've got.

**Time budget:** 2 hours for the first complete pass. ~30 min setup, ~60 min
manual testing, ~30 min logging issues to GitHub.

---

## Phase 1: Setup (~30 min)

### Step 1: Install the toolchain

```bash
# Install Aftman (manages Rojo + Wally + Selene + StyLua versions)
curl -L https://github.com/LPGhatguy/aftman/releases/latest/download/aftman-macos.zip | tar xz
sudo mv aftman /usr/local/bin/

# From the repo root
cd ~/dev/nextops/nextops-founder-mode-roblox
aftman install   # Reads aftman.toml, installs Rojo 7.4.4, Wally 0.3.2, etc.

# Confirm
rojo --version
wally --version
selene --version
```

Expected: all three commands print version numbers. If any fail, debug
PATH (Aftman's tools install to `~/.aftman/bin/`).

### Step 2: Install Roblox Studio

If you don't already have it:
- macOS: download from https://create.roblox.com/desktop-app
- Windows: same URL
- Sign in with the Roblox account that will own the dev/staging place

### Step 3: Install the Rojo plugin in Studio

- Open Roblox Studio (don't open any place yet)
- Click "Plugins" tab → "Find Plugins" → search "Rojo" → install Rojo by Roblox
- This is the bridge that lets your local repo sync into Studio

### Step 4: Start the local Rojo server

```bash
cd ~/dev/nextops/nextops-founder-mode-roblox
rojo serve default.project.json
```

Expected output: `Rojo server listening: http://localhost:34872/`. Leave
this terminal running for the duration of the playtest.

### Step 5: Connect Studio to Rojo

- Open Roblox Studio → Baseplate template (any blank template works)
- Plugins tab → Rojo → Connect
- Default address `localhost:34872` → click Connect
- Studio's Explorer panel should populate with your file structure:
  ServerScriptService/Init.server.lua + Systems/, ReplicatedStorage/Modules
  + Config + Remotes, StarterPlayer/StarterPlayerScripts/UI

**Stop here if Studio doesn't connect.** Common causes:
- Rojo server not running (re-run `rojo serve`)
- Plugin not installed correctly (re-add via Plugins tab)
- Firewall blocking localhost (rare on dev machines)

### Step 6: Save place to Roblox

Once Rojo-synced, click File → Publish to Roblox As → select your dev/staging
place (or create new). This is what `ROBLOX_STAGING_PLACE_ID` should point to.

---

## Phase 2: First-run smoke test (~60 min)

### Test A: Server starts cleanly (5 min)

- Press F5 (or Test → Play) to enter test mode
- Open Output panel (View → Output)
- Look for the `[FounderMode]` init logs in order:

Expected log sequence (simplified):
```
[FounderMode] Server starting...
[FounderMode] Remotes initialized.
[ProfileWrapper] Loaded profile for <YourUsername> (capital=500, regulars=0).
[Economy] Initialized.
[FounderMode] AntiExploit initialized.
[DayNightCycle] Initialized. 1 real-min = ~60 game-min. Currently day 0, hour <X>.
[NPC] Customer arrival system online.
[Dialogue] Customer-discovery dialogue handler online + GetNpcWant wired.
[DayReport] Build-Measure-Learn loop online.
[BuildMode] Place/Move/Rotate handlers online.
[Stocking] Inventory ↔ container bridge online.
[PivotEvents] Pivot-vs-Persevere escalation system online.
[Stokvel] DISABLED pending Roblox policy clearance.
[Snapshot] GetProfileSnapshot + GetGameTimeSnapshot RemoteFunctions ready.
[RandomEvents] Three hand-tuned events scheduled...
[FounderPass] 30-tier pass online.
[DailyLogin] 7-day Stokvel-Week rotation online.
[Prestige] Graduation loop online.
[MarketplaceBridge] ProcessReceipt + Game Pass listener wired (idempotent).
[Idle] Welcome-back-revenue layer online.
[Leaderboards] 3-view OrderedDataStore-backed leaderboards online.
[TestHarness] Ready. Studio chat commands: /profile /buy /sell /price /reset /place /placed /capacity /stock /shelves
[FounderMode] Server ready.
```

**ANY warn() or red error in the output = bug.** Log it (see Phase 3).

### Test B: Client UI loads (3 min)

Once in Play mode, on the player's screen you should see:
- Top-bar HUD: `💵 R— CAPITAL  📦 — ON SHELF  📣 — SIGNAGE  Day 0 — XX:XX`
  (the dashes will populate after first server poll, ~1.5 sec)
- Top-right: 🎫 Founder Pass toggle button
- Console output: `[HUD] Top-bar HUD ready.` + `[FounderPassPanel] Pass icon ready` +
  `[Onboarding] Welcome, <YourUsername>!` + `[DialoguePanel] Mobile-first dialogue UI ready.` +
  `[DayReportPanel] Mobile-first Day Report UI ready.`

If any UI is missing → log as bug.

### Test C: Chat command harness (15 min)

In the in-game chat (press `/` to open), test each command:

| Command | Expected output | What it proves |
|---|---|---|
| `/profile` | Profile snapshot in F9 console: capital=500, inventory=0, regulars=0, spazas=1, prestige_lvl=0 | ProfileWrapper loaded |
| `/buy bread 5 3` | "+5 bread @ R3" log; capital drops to R485 | Economy.onBuyStock + AntiExploit OK |
| `/profile` | Inventory shows `1. bread × 5 @ R3.00` | Persistence working |
| `/place shelf-wood-2tier 5 1 0` | Log: "placed shelf-wood-2tier at (5,1,0)"; capital R485 → R305 | BuildMode + SpazaItems lookup OK |
| `/placed` | Lists 1 placed item with instanceId | BuildMode.getPlacedItems works |
| `/capacity` | "8 shelf slots, 0 signage strength" | Capacity computation OK |
| `/stock bread <instanceId> 3` | (use the instanceId from /placed) "stocked 3 × bread" | Stocking.assignToContainer OK |
| `/shelves` | "bread × 3" | Stocking.getOnShelfStock OK |
| `/price bread 8` | "set bread price to R8.00" | Economy.onSetPrice + AntiExploit price-floor/ceiling OK |
| `/buy ice-cream 5 10` | (perishable) Should succeed; ice-cream goes into inventory | Inventory accepts perishables off-shelf |
| `/stock ice-cream <shelfId> 1` | Should FAIL with `perishable_needs_cold_storage` | Stocking perishable rule fires |

**ANY of these failing or behaving wrong = log a bug.**

### Test D: NPC arrival (15 min)

Wait or scrub time (no scrub mechanism in v0.x — actual real wait).

Within ~3 minutes you should see the first NPC spawn:
- Console: `[NPC] Mama Thandi arrived at <Username>'s spaza wanting <product> (...)`
- In the world: a bright-orange Part with "Mama Thandi" floating-text label

Click on Mama Thandi:
- Console: `[Dialogue] ...`
- A dark panel appears with the NPC's name + 3 dialogue branches
- Click the gold branch (specific past-behavior question)
- The NPC response appears in the same button slot for 2s
- Panel transitions to a Sell prompt: "They want <product>"
- Tap Sell → log: `[Economy] sold <product> for R(price × 3) (×3.0 gold-talk reward)`

**This is the customer-discovery curriculum loop firing end-to-end. If
it works, the entire Pillar 3 pedagogy is shippable. If it doesn't, log
specifically WHERE in the chain it breaks (NPC didn't spawn? Click did
nothing? Dialogue panel empty? Sell button no-op? Revenue not credited?).**

### Test E: Day rollover + DayReport (10 min)

Force a day rollover. v0.x ships at 24 real-min per game-day, which is too
long to wait. Quick test mod: in ServerScriptService → Init.server.lua,
TEMPORARILY change the game-day-compression in DayNightCycle from
`24 * 60` to `2 * 60` (2-min game-day for testing). Save, Studio re-syncs.
Re-run Play.

Within ~2 minutes you'll see:
- Console: `[DayNightCycle] In-game day 0 ended. Day 1 started.`
- Console: `[DayReport] <Username> — Day 0. Sold X items. Revenue R<n>. Profit R<n>. <m> unmet wants.`
- Day Report panel slides in from off-screen with three columns

**REVERT THE TIMING CHANGE before committing.** This was a temporary debug aid.

### Test F: RandomEvents (10 min)

Set the day to 7 (which triggers LoadShedding) by adjusting the test-mod:
in DayNightCycle, force `getCurrentDay()` to return 7 temporarily.

Within 5 sec of fake day-7 firing:
- Console: `[RandomEvents] LoadShedding starting. Duration: 10800 sec game-time.`
- (No visual effect yet — that's the `client/lights.lua` work eKasi has but
  Founder Mode hasn't ported. Logging-level test only for v0.x.)

After ~60 real-sec at fake day-7:
- Console: `[Stocking] <Username> lost X perishable units from container ... (load shedding)`
  (only if the player has perishable items in a powered fridge)

---

## Phase 3: Bug logging (~30 min)

For each issue found, open a GitHub issue with this template:

**Title:** `[playtest-bug] <terse description>`

**Body:**
```
## What I tested
<command or action sequence>

## Expected
<what the test checklist said should happen>

## Actual
<what happened — include console logs verbatim>

## Console logs (verbatim)
\`\`\`
<paste F8/F9 console output>
\`\`\`

## Repro steps
1. ...
2. ...

## Environment
- Studio version: <File → About>
- OS: macOS / Windows
- Date: <today>
```

Tag with labels: `playtest-bug`, `v0.x`, severity (`critical` if blocks
testing further, `high` if breaks a feature, `medium` for visual/polish,
`low` for ideas).

**Common bug categories to expect on first playtest** (most teams hit):
- Some module init fails silently because of a Wally dep that didn't
  install (ProfileService stub fallback path activates — verify with
  console "STUB profile store" warning)
- One client UI doesn't load because of a typo in `Remotes.get(...)` call
- An NPC spawns inside the ground (placement Y coord wrong)
- Anti-exploit rate limiter throttles a legit chat command (`SetPrice`
  has the tightest rate of 2/sec; in fast testing this trips)

---

## Success criteria for first playtest

You'll know it went well if you can answer YES to all of these:

- [ ] Server initializes all 19 systems without red errors
- [ ] All 3 client UIs render
- [ ] At least 5 of the 11 chat commands work without errors
- [ ] At least one NPC spawns and is clickable
- [ ] Sell action successfully credits capital
- [ ] Day rollover fires Day Report panel

If 4-5 of these pass, v0.x is in solid shape; the bugs are addressable.
If 0-2 pass, there's a structural issue — log everything and we'll dig in.

If you get further (the customer-discovery loop fires gold-quality, you
see your name on Leaderboards via a /capacity-style chat command, etc),
v0.x is genuinely SHIPPABLE as a closed beta. That's significantly ahead
of expectation.

---

## After playtest — what to do next

1. **Commit any debug-mod-revert changes** (DayNightCycle compression back to 24 min)
2. **Open the GitHub issues** for each bug found (use the template above)
3. **Trigger eKasi staging deploy** (push any commit; it auto-fires)
4. **Send the Roblox developer-relations stokvel-policy inquiry** (the email
   draft lives in `Founder-Mode-Validation-Kit/05-Roblox-Stokvel-Policy-Email.md`)
5. **Hire the 3D artist** (per `01-3d-artist-commission.md`)

The first playtest is the moment Founder Mode stops being theory and
becomes evidence. Until you press Play, you've been building blind.
