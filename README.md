# NextOps Curriculum

Open startup-and-tech curriculum delivered through Founder Mode gameplay.

**License:** CC-BY-NC-SA 4.0 — free to read, share, adapt for non-commercial use, with attribution. Commercial use requires permission.

**Mission:** teach the entire skill stack of starting a tech-enabled business — problem-solving, critical thinking, lean startup, business models, design thinking, customer discovery, technology fundamentals, hardware, robotics, IoT, AI, ethics, ops, hiring, fundraising — through a game that never feels like school.

This repo is the **single source of truth** for the curriculum and is referenced by every NextOps Studios product (Founder Mode Roblox, Mzansi Foundation Pack on Tebex, future hardware/AR companion experiences).

## Structure

```
curriculum/
├── 00-overview.md                    # The v1-complete curriculum spine
├── 01-startup-curriculum.md          # Lean startup, BMC, customer discovery, pivot, etc.
├── 02-problem-solving.md             # First-principles thinking, root cause, debugging
├── 03-critical-thinking.md           # Decision under ambiguity, mental models
├── 04-tech-fundamentals.md           # Coding, robotics, IoT, AI as gameplay mechanics
├── 05-business-models.md             # Subscription, marketplace, reseller, SaaS, etc.
├── 06-real-world-bridge.md           # How in-game lessons transfer to actual life
├── 07-pedagogy-design-rules.md       # The "never feels like learning" rules
├── concepts/                         # Daily curriculum-agent deep-dives
│   ├── customer-discovery.md
│   ├── unit-economics.md
│   ├── ...
└── design-docs/                      # Migrated from earlier office-hours sessions
    ├── founder-mode-design.md
    ├── market-gap-audit.md
    └── ...
```

## How the curriculum agent works

A scheduled remote AI agent fires every weekday morning. Each fire:

1. Picks a curriculum concept that hasn't been deep-dived yet (or revisits one that needs an update).
2. Writes a deep-dive markdown file under `curriculum/concepts/`.
3. Drafts how the concept maps onto Founder Mode gameplay — a specific NPC interaction, a specific Day Report consequence, a specific business mechanic.
4. Opens a GitHub issue tagged `curriculum-review` with the day's deep-dive and 1-2 questions for human review.

The human (you) reviews when convenient, edits the markdown, closes the issue. Curriculum compounds daily without daily human work.

## v1-complete principle

The full startup curriculum ships in v1. What staggers across versions is the **expression** of the curriculum:

- **v1 — Spaza Tycoon (one business)** teaches the FULL curriculum through one business deeply.
- **v2-v6** add new businesses (salon, taxi rank, scrapyard, gas reseller, robotics club) that each express the SAME curriculum through different lenses, plus introduce new tech (QR, IoT, sensors, code blocks).

A v1 player who finishes the spaza arc has been exposed to every concept in the curriculum. v2+ deepens, doesn't add new fundamentals.

## Real-world bridge

Founder Mode is not just a game. Pokémon GO's lesson: digital experiences that touch the real world have 10x emotional staying power. v1 ships modest hooks; v3+ builds a full companion-app + AR + IRL-challenge layer.

## Contributing

This is currently solo-led by Nkululeko Khoza (NextOps Studios). Pull requests on the curriculum docs are welcome from educators and entrepreneurs who want to refine the lesson trees. Game-product code lives in separate repos (`nextops-ekasi-loadshedding`, `nextops-founder-mode-roblox`, etc.) and is closed-source until ship.
