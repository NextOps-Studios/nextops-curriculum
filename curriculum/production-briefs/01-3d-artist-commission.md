# 3D Artist Commission Brief — Founder Mode v0.x Starter Assets

**Goal:** the smallest set of 3D models that, when imported into the existing
Roblox build, makes the world feel real instead of placeholder. Optimized for
budget (R8,000-15,000 / ~$450-850 total) and timeline (10-14 days from
hire to delivery).

**Target file format:** Roblox `.rbxm` model files OR `.fbx` we can import into
Roblox Studio ourselves. Texture format: 1024×1024 PNG max per object.
Polygon budget: ≤ 1,500 tris per item to hit the mid-tier Android 30fps
target locked in design 1.4A.

**Cultural authenticity is non-negotiable.** Every model must read as kasi
(Soweto, Khayelitsha, Mamelodi vibe) — NOT generic-suburban-American.

---

## Tier 1 — Must-have for v0.x playtest (budget: R5,000-8,000)

### 1. Soweto Street Block (1 large set)

A single ~80×80 stud street segment that becomes the player's plot environment.

Required pieces:
- Tarred main road (segmented so the road's center line is aligned)
- Two-lane curb + pavement on each side
- 2 streetlight poles (animated dim/lit states for load-shedding event)
- 1 corner-shop facade (where the player builds their spaza inside)
- Empty plot area (~40×40 stud build zone, fenced lightly to mark boundary)
- 1 distant-Joburg-skyline backdrop (low-poly, never-walked-to)
- Optional: scattered clutter — tyre stack, paint can, plastic crate

Style references:
- Photo references: search "Soweto street day" + "Khayelitsha township main road"
- Colour palette: warm dusk-orange, dust-grey, terracotta accents, NOT gleaming-grey concrete
- Lighting baked for golden-hour (Roblox in-game lighting takes over)

Reference budget: R3,500-5,000 from Fiverr Pro / Behance / SA-local 3D artist.

### 2. Spaza Shop Interior Kit (5 items)

Drop-in interior pieces that fit inside the facade.

- Wooden shelf (2-tier) — 3×4×1 stud size; texture: untreated pine + scuffed
- Metal shelf (3-tier) — 3×5×1 stud size; texture: galvanized steel + dust
- Half-bar fridge — 2×3×2 stud size; texture: white-painted metal + branding
  decals (custom, NOT real Coca-Cola — use generic "Cool Drinks" lettering)
- Wooden counter — 4×3×2 stud size; with cash drawer detail; texture:
  varnished wood + sticker decals
- Hand-painted wall sign — 6×2×0.1 stud size; texture: peeling paint with
  hand-lettered "FRESH BREAD INSIDE" or similar generic kasi signage

Reference budget: R1,500-3,000 (5 items × R300-600 each).

---

## Tier 2 — Enhancement for v0.x polish (budget: R3,000-7,000)

### 3. NPC Character Outfit Pack (10 outfits, 1 per named regular)

Each outfit must read as the archetype from `Config/NPCs.luau`. Roblox has
free Character Customization tools; we don't need full character meshes,
just clothing texture sheets.

- Mama Thandi: Sunday dress + doek headscarf, plastic shopping bag accessory
- Bra Sipho: reflective taxi-driver jacket, Bafana cap, faded jeans
- Sizwe: school uniform untucked, takkies, old backpack
- Aunty Refilwe: church dress + church hat, Bible bag accessory
- Lerato: nurse uniform, comfy shoes, lanyard with hospital badge
- Bra Vusi: branded racing tee, oil-streaked hands, mechanic apron
- Mama Buyi: salon apron, hair in wrap
- Tebogo: security-firm uniform, peaked cap, walkie-talkie
- Zinhle: streetwear-chic + ring light in backpack + gold hoops
- Bhuti Khaya: office shirt, glasses, large shopping bag

Format: Roblox-native shirt + pants UV maps (1024x1024 PNG each).
Reference budget: R2,000-3,500 (10 outfits × R200-350 each).

### 4. Audio asset commission (separate from 3D, list it here for completeness)

Not 3D-modelable but ship with the same artist budget for coordination:

- 5 amapiano background loops (royalty-free OR commissioned at R500-1,000 each)
- 12 NPC voice clips (1 generic + 1 specific per named regular, ~3-5 sec each)
- 5 ambient sounds (hadeda calls, taxi hooter, distant alarms, generator hum,
  township morning ambience)

Reference budget: R2,000-4,000. Recommend Voice123 SA voice talents at
R200-400 per clip + Pixabay/Mubert for background loops.

---

## Sourcing the artist

**Recommended: SA-local Fiverr Pro artist or Behance freelancer**

Search terms on Fiverr / Behance / Upwork:
- "Roblox Studio environment artist"
- "Low-poly stylized environment Soweto South Africa"
- "Mobile-game-optimized Roblox assets"

**Vetting questions to ask before hiring:**
1. Have you shipped Roblox-Studio-targeted assets before? (Show portfolio)
2. Are you familiar with Roblox's polygon budget for mobile (≤1,500 tris)?
3. Can you deliver in `.rbxm` directly OR `.fbx` we can import?
4. Have you done African / SA cultural assets before? (cultural-authenticity check)
5. What's your turnaround for Tier 1 (Street Block + Interior Kit)?

**Red flags** (do NOT hire):
- Portfolio is all American suburbs / Western fantasy
- Doesn't know what Rojo / Roblox Studio is
- No mobile-poly-budget awareness
- Quotes substantially under R3,500 for the Tier 1 set (likely AI-generated)

**Backup plan** if hire delays: use the Roblox Marketplace's free assets +
generated Midjourney textures applied to primitives. Quality drops; v0.x
playtest still works for evaluating the gameplay loop.

---

## Delivery checklist

Before paying the artist, verify:

- [ ] All assets import into Roblox Studio without errors
- [ ] All textures are ≤ 1024×1024 PNG
- [ ] All meshes are ≤ 1,500 tris each
- [ ] Each item has a `Configuration` child with the corresponding
      `SpazaItems.luau` ID as a StringValue (so BuildMode can match
      placed-item → 3D model)
- [ ] Each NPC outfit ships with proper Roblox shirt + pants assets
- [ ] At least one full-scene render at golden hour (Soweto vibe check)
- [ ] License grants NextOps Studios full commercial rights to use,
      modify, redistribute (including in published Roblox games)

---

## Integration into the existing repo

Drop delivered assets into:

```
nextops-founder-mode-roblox/
├── assets/                          # NEW directory
│   ├── street-block/                # Tier 1 #1
│   ├── spaza-interior/              # Tier 1 #2
│   ├── npc-outfits/                 # Tier 2 #3
│   └── audio/                       # Tier 2 #4
```

Then in `default.project.json`, add:

```json
{
  "Workspace": {
    "$path": "src/Workspace",
    "StreetBlock": { "$path": "assets/street-block/StreetBlock.rbxm" }
  },
  "ServerStorage": {
    "$path": "src/ServerStorage",
    "SpazaModels": { "$path": "assets/spaza-interior" },
    "NPCModels": { "$path": "assets/npc-outfits" }
  }
}
```

Then `BuildMode/init.luau`'s `ServerStorage.SpazaModels.<modelName>` lookup
automatically resolves the catalog item → real 3D model.

---

## Budget summary

| Tier | Item | Low | Mid | High |
|---|---|---:|---:|---:|
| 1 | Soweto Street Block | R3,500 | R4,500 | R5,500 |
| 1 | Spaza Interior Kit (5 items) | R1,500 | R2,250 | R3,000 |
| 2 | NPC Outfit Pack (10) | R2,000 | R2,750 | R3,500 |
| 2 | Audio commission (~22 clips) | R2,000 | R3,000 | R4,000 |
| **Tier 1 only (minimum playtest)** | | **R5,000** | **R6,750** | **R8,500** |
| **Tier 1 + 2 (full v0.x)** | | **R9,000** | **R12,500** | **R16,000** |

Recommend starting with **Tier 1 only** (R5,000-8,500). Reach playtest with
Tier 1 done; commission Tier 2 once playtest signals confirm gameplay
direction. Don't pre-spend Tier 2 capital before validating Tier 1.
