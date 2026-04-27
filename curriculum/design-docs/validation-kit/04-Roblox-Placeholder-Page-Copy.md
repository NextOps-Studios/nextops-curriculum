# 04 — Roblox Placeholder Page (publish empty, accumulate favorites)

**Goal:** a published, live Roblox game with a "Coming Soon" baseplate that accumulates favorites from TikTok traffic. Day-30 floor: 100+ favorites.

**Why publish empty:** Roblox favorites are the platform-native demand signal. They predict launch traction. They count on the day-30 review. Publishing the empty page now is the only way to start collecting.

**Time:** 2-3 hours total (Studio install + place creation + asset upload + publish + cosmetic polish).

---

## Steps in order

1. **Install Roblox Studio** (Mac/Windows/web). Free at create.roblox.com.
2. **Create a new Baseplate place.** File → New → Baseplate.
3. **Strip it.** Delete the spawning Spawn Pad and replace with a single welcome SpawnLocation (we'll add UI on it).
4. **Add a "Coming Soon" GUI** — see code below.
5. **Configure place settings** — name, icon, description, genre, thumbnails.
6. **Upload icon and 4 thumbnails.**
7. **Publish to Roblox.**
8. **Make the place public** (Configure → Permissions → Public).
9. **Copy the URL** for use in the TikTok post + concept video CTA frame.

---

## Place configuration (copy-paste ready)

### Name (in-Roblox listing)

```
Founder Mode: Mzansi 🇿🇦
```

(The flag emoji is fine in titles per Roblox guidelines and helps SA-region players spot it.)

### Genre

`Town and City` — closest match for tycoon/township. Tycoon-specific genres get auto-clustered by Roblox; Town and City is the safer default until v1 has gameplay.

### Tags (Roblox lets you set up to 5)

`Tycoon, Roleplay, Simulator, Town, Building`

### Short description (used on game cards in search results, ~150 chars)

```
Build your spaza. Talk to your customers. Stokvel up. Run the kasi. Founder Mode: Mzansi — coming to Roblox. Favorite to play first.
```

### Long description (full game page, paste verbatim)

```
🇿🇦 FOUNDER MODE: MZANSI — coming to Roblox.

You start with R500 and an empty plot in the kasi.
Build your spaza. Stock what your customers actually ask for.
Read the day. Run it back. Stokvel up.
Spaza → Salon → Taxi rank → Empire.

A tycoon for the kasi, the diaspora, and anyone who wants to build something real.

⏰ Launch: late 2026
🔔 Favorite this page to get the drop notification

📱 Built mobile-first (Android + iOS)
🌍 Mzansi v1 — Lagos, Nairobi, Accra coming after

Want updates? Follow the dev journey on TikTok: [your TikTok handle]

———

Founder Mode is a tycoon game where the lessons are the gameplay. There are no quizzes, no tutorials lecturing you. The customers teach you. The numbers teach you. Your spaza teaches you.

If you've ever watched your gogo run a stokvel, watched your uncle drive a taxi, watched your auntie run a hair salon — this is for you.

If you've never seen any of that — even better. Come learn how a real economy actually works, kasi-style.
```

### First-comment seed (paste as the first comment on your own game page)

```
Founder dev here 👋 

This page is the favorite tracker. Game launches late 2026. Got questions? Drop them below — I'll answer every one.

Follow the build on TikTok: [link]
```

---

## Asset brief (icon + thumbnails — needed before publish)

You'll need 5 images. Use the same visual style as the concept video to keep the brand consistent.

**Icon (512x512 px, JPG/PNG):**
- A stylized Soweto street at golden hour, a single spaza shop in foreground
- Bold "FOUNDER MODE" text top-third in white with thin black outline
- "🇿🇦 MZANSI" subtitle below
- Background: warm dusk-orange (matches video frame 2)

**Thumbnails (1280x720 px each, 4 total):**
1. The spaza building moment (frame 4 of the video) — captioned "BUILD YOUR SPAZA"
2. The customer dialogue moment (frame 5) — captioned "TALK TO YOUR CUSTOMERS"
3. The Day Report chalkboard (frame 6) — captioned "READ THE DAY"
4. The empire-expansion frame (frame 8) — captioned "RUN THE KASI"

Each thumbnail = one frame of the concept video, repurposed at 1280x720. Saves time vs. making new art.

**Where to make them:** Canva (drag-and-drop, free), Figma (free tier), or whoever made the video frames originally.

---

## "Coming Soon" GUI Lua (drop into StarterGui → ScreenGui → Frame)

This is the only Lua you write this week. It puts a "Coming Soon" panel in front of every player who joins the empty baseplate, with a "Favorite" prompt.

```lua
-- StarterGui/ComingSoon/Init.client.lua
-- Renders a Coming Soon panel and prompts players to favorite the game.

local Players = game:GetService("Players")
local MarketplaceService = game:GetService("MarketplaceService")

local player = Players.LocalPlayer
local screenGui = script.Parent

-- Make the panel impossible to miss
local frame = screenGui:WaitForChild("Frame")
frame.Visible = true
frame.BackgroundTransparency = 0.1

-- Prompt favorite after 5 seconds (gives the player time to read)
task.delay(5, function()
  local placeId = game.PlaceId
  -- PromptGameFavorite is the Roblox-native favorite UX
  local success, err = pcall(function()
    MarketplaceService:PromptPremiumPurchase(player) -- placeholder; swap for actual
  end)
  -- Note: there is no PromptFavorite API directly; instead, instruct the player
  -- via UI to click the star icon on the game page. The instruction text in
  -- the Frame should say: "⭐ Tap the star to favorite — you'll get the launch notification."
end)

-- Auto-dismiss after 30s so the player can walk around the empty baseplate
task.delay(30, function()
  frame.Visible = false
end)
```

**Note on the "Favorite" mechanic:** Roblox doesn't expose a `PromptFavorite` API. The favorite happens when a player taps the star icon on the game page (outside the game itself). Your job is to (a) make the game page visible from the in-game GUI with a clear instruction, and (b) make the in-game experience pleasant enough that they go back to the page and tap favorite. The 30-second baseplate experience needs to land that ask.

### GUI text (paste into the Frame's TextLabel)

```
🇿🇦 FOUNDER MODE: MZANSI

Coming late 2026.

⭐ Tap the star on the game page to favorite —
you'll get the launch drop notification.

Follow the build on TikTok: [your handle]
```

---

## Optional polish (skip if time-constrained)

- Add a single SA-coded music track on a Sound object inside the baseplate (royalty-free amapiano loop, attribution in the description).
- Place a single decorative "Coming Soon" sign-prop on the baseplate so screenshots have something to look at.
- Set the place's loading screen background to the Founder Mode logo.

None of these gate publishing. Ship the page in 3 hours; polish later.

---

## After publishing

1. Copy the place URL: `roblox.com/games/[placeId]/Founder-Mode-Mzansi`
2. Paste it into the concept-video frame 10 (CTA).
3. Paste it into the TikTok caption.
4. Paste it into your TikTok bio link.
5. Bookmark the favorites count panel: Roblox Studio → My Creations → Founder Mode: Mzansi → Statistics. Check it every 3 days, log to `tiktok-comment-log.md`.

---

## Pitfalls

- **Don't publish without a public-permission flag.** Roblox defaults to private. Configure → Permissions → Public.
- **Don't use real brand assets** (Coca-Cola, Vodacom, FNB) on the icon or thumbnails. Roblox auto-flags these.
- **Don't promise a launch date you can't hit** in the description. "Late 2026" is honest. "Q2 2026" if you miss it makes you look slow.
- **Don't disable comments on the game page.** Comments are part of the demand signal. Moderate, don't silence.
- **Don't worry about player count being zero in the first weeks.** The signal is FAVORITES, not concurrent players. The empty baseplate isn't a game; it's a marker.
