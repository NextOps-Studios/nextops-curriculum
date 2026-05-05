# Week-1 Execution Plan — From Code-Complete to Live Playtest

This is the unified plan that ties together GitHub Secrets + Hetzner provisioning
+ Roblox Studio playtest + 3D artist hire + curriculum agent firing + the May-11
validation check-in.

**You are here:** code is at v0.x architectural completeness. NEXT: get
secrets in, server provisioned, Studio playtested, artist hired. All within
~7 days.

---

## Day 1 (today)

### Morning — Secrets + provisioning (~45 min)

```bash
# 1. Gather what you need (5 min)
ssh-keygen -t ed25519 -C "nextops" -f ~/.ssh/id_ed25519   # if missing
cat ~/.ssh/id_ed25519.pub        # copy this for SSH_PUBLIC_KEY
cat ~/.ssh/id_ed25519            # copy this for SSH_PRIVATE_KEY

# 2. Hetzner: hetzner.com → Console → New Project "nextops" → API Tokens → Generate
# 3. CFX: keymaster.fivem.net → New License → "GTA V" + "Recurring" → use 127.0.0.1 IP
# 4. Discord: Settings → Integrations → Webhooks → New Webhook → copy URL

# 5. Run the helper
cd ~/dev/nextops/nextops-ekasi-loadshedding
./deployment/setup-github-secrets.sh
# Paste each secret when prompted. Skip Tebex / Roblox keys for now (Enter).

# 6. Verify
gh secret list --org NextOps-Studios

# 7. Trigger Provision
gh workflow run provision-server.yml \
  --repo NextOps-Studios/nextops-ekasi-loadshedding --ref main

# 8. Watch
gh run watch --repo NextOps-Studios/nextops-ekasi-loadshedding
```

Expected: in ~3 minutes, Hetzner FiveM dev server is provisioned, IP set
as repo secret, Discord webhook posts the IP + SSH command.

### Afternoon — First Roblox Studio playtest (~2 hr)

Follow `03-first-studio-playtest.md` step-by-step. Expected: 4-5 of 6 success
criteria pass; you log 5-15 GitHub issues for bugs found.

This is the most important 2 hours of week 1. Until you've actually pressed
Play in Studio, every line of code we've shipped is theoretical.

---

## Day 2 — Bug fixes from playtest (~3 hr)

For each `playtest-bug` issue logged yesterday:

1. Reproduce in Studio (Rojo serve still running from yesterday)
2. Fix in the source file
3. Save → Studio auto-resyncs via Rojo plugin
4. Re-test
5. Commit with message referencing the issue: `fix: <bug> (closes #N)`
6. Push → CI verifies → close the issue

Expected: 5-10 fixes shipped today. Each fix is small (the architecture is
sound; bugs at this stage are typo-level).

---

## Day 3 — 3D artist hire kickoff

Following `01-3d-artist-commission.md`:

```
Morning:
  - Post the Tier-1 commission spec to Fiverr Pro / Behance / a SA-local
    Roblox-focused freelancer Discord
  - Vet 3-5 candidates against the questions in the brief
  - Hire one for R5,000-8,500 Tier-1 budget

Afternoon:
  - Send the Roblox developer-relations stokvel-policy inquiry email
    (draft lives in Founder-Mode-Validation-Kit/05-Roblox-Stokvel-Policy-Email.md)
  - Track in a 'roblox-policy-pending' GitHub issue with the date sent
```

---

## Day 4-5 — eKasi smoke-test on staging (~2 hr each day)

While waiting for 3D artist + Roblox-policy response:

```bash
# Trigger the eKasi staging deploy by pushing any small change
cd ~/dev/nextops/nextops-ekasi-loadshedding
echo "" >> README.md
git add README.md
git commit -m "deploy: trigger first staging deploy"
git push origin main
```

Watch the deploy workflow. Expected: ~90 sec end-to-end. Discord webhook
posts deploy success.

Then connect to the Hetzner FiveM server in your FiveM client (use the IP
from `gh secret list` or Discord). In F8 console:
```
/ekasi-status
/ekasi-stage 4    (force stage 4)
```

If lights dim + alarms ring + NPCs panic + phone notification fires →
eKasi is end-to-end working in production.

---

## Day 6 — Validation interviews (~3 hr)

Per the eng-review locked Tension E: text 3 Roblox-aged kids (9-15) with
the 30-second concept video. Use the kid-interview kit in
`Founder-Mode-Validation-Kit/02-Kid-Interview-Kit.md`.

Save each verbatim answer to:
`~/Desktop/Founder-Mode-Validation-Kit/kid-interview-{name}-{date}.md`

After all 3, write the synthesis doc per the kit's instructions.

---

## Day 7 — Weekly review prep + roadmap update

The Weekly Review remote agent fires Monday 08:07 SAST. Before it does:

1. Close any remaining `playtest-bug` issues from days 1-2
2. Update the roadmap doc if anything material shifted (kid interviews said
   pivot? 3D artist quoted higher? Roblox policy declined?)
3. Open a GitHub issue summarizing your own week-1 retrospective

The Monday agent reads all of the above + closed issues + commit history
+ daily-brief outputs and writes a synthesis. You close it after reviewing.

---

## Calendar overview

| Day | Activity | Hours | Blockers |
|---|---|---:|---|
| 1 | Secrets + provision + Studio playtest | 3 | Hetzner account |
| 2 | Bug fixes from playtest | 3 | Day-1 bug log |
| 3 | Artist hire + Roblox policy email | 2 | Cash for R5,000-8,500 hire |
| 4 | eKasi staging smoke-test | 2 | — |
| 5 | eKasi balance tuning + Tebex storefront prep | 2 | Day-4 results |
| 6 | 3 kid validation interviews | 3 | Access to Roblox-aged kids |
| 7 | Weekly review prep + Day-7 retrospective | 2 | — |
| **Total** | | **~17 hr** | |

That's the realistic week-1. ~17 hours of focused founder-time gets you
from "code complete" to "live staging deploy + validated demand signal +
artist commissioned + Roblox policy inquiry filed."

---

## Decision gates (what stops the build vs. what continues)

After day 7, three signals determine if Founder Mode v1 build kicks off in
month 2:

1. **Roblox policy clearance for stokvel** — green light, conditional, or
   declined. If declined, cut stokvel from v1 entirely.
2. **Kid validation interviews** — at least 2 of 3 say "yes I'd play this"
   with specific reasons OR the wedge needs sharpening before more code
3. **eKasi staging health** — if FiveM crashes / disk fills / ESX/QBCore
   integration fails, fix BEFORE shipping more eKasi to Tebex production

If all three signals are green by day 30 → start the v1 art-and-content
production sprint (months 2-7) per the design doc.
If any signal is red → pause and revisit the design doc.

The May 11 check-in remote agent will ask you about all three on day 14.

---

## What this plan deliberately does NOT include

- More Founder Mode code (we've passed the "more code helps" threshold)
- More retention-spine systems (already at 7/9)
- More curriculum exemplars (the agent has 5; that's enough quality bar)
- The sprint-execution plan beyond day 7 (the May-11 check-in is the next
  decision gate; planning past it pre-validation is wasted effort)

This plan is **deliberately scoped to validation, not production**. The
production-content sprint starts only after validation signals are in.
