# 06 — Roblox DevEx + W-8BEN Paperwork (background track)

**Goal:** complete the prerequisites to receive USD payouts from Roblox in the future. Multi-week processing time means start now even though no Robux earnings exist yet.

**Why now:** when v1 launches and Robux start coming in, you don't want to discover your DevEx eligibility is blocked by paperwork that takes 6-8 weeks to clear. Get it done while the game is in pre-production.

**Time investment:** ~2 hours of your time spread across 2-4 weeks of waiting/processing.

---

## What DevEx is (one line)

**DevEx** (Developer Exchange) is Roblox's program that converts Robux earnings into real USD that gets paid into your bank account. It's the only path to actually getting paid for your game.

**Current rate (verify on Roblox before relying on it):** ~0.0035 USD per 1 Robux. So 1,000 Robux = ~$3.50. Minimum payout threshold = 50,000 Robux (~$175). Rates and thresholds change; check the Roblox Creator Hub for current numbers.

---

## Eligibility prerequisites

You must hit ALL of these before DevEx will pay out:

| # | Requirement | Status | Action |
|---|---|---|---|
| 1 | Roblox account ≥ 13 years old | Default for SA-resident adult | none |
| 2 | Roblox account in good standing (no warnings/bans) | Check at roblox.com/my/account | review |
| 3 | Roblox Premium subscription active | $4.99/month minimum | subscribe |
| 4 | ID verification completed | KYC via Persona inside Roblox | submit |
| 5 | Tax form on file (W-8BEN-E for SA-resident sole proprietor or W-8BEN for individual) | IRS-required for US-source income | submit |
| 6 | Minimum 50,000 Robux balance | Earned via Game Pass / Dev Product / Premium Payouts in your game | future |

Items 1-5 can be done now without any game launched. Item 6 is the actual launch milestone.

---

## Step-by-step (in order)

### Step 1 — Activate Roblox Premium (~5 min, ~R100/month)

- Go to roblox.com/upgrades/premium
- Select the lowest tier (Premium 450 Robux/month or equivalent)
- Pay via credit/debit card
- Premium activation is instant
- Note: as a developer, Premium gives you Premium Payouts visibility in your future game's analytics, plus DevEx access. Treat it as a business expense.

### Step 2 — Verify your identity (~30 min)

- Go to roblox.com/account/settings
- Scroll to "Verification"
- Click "Verify with Persona"
- You'll need: a government-issued photo ID (SA driver's license or passport), and a webcam/phone camera for the live selfie check
- Persona processes in ~24-48 hours for most SA submissions
- Outcome: a green "Verified" badge on your account

### Step 3 — Determine your tax form (W-8BEN vs W-8BEN-E)

You're a South African resident receiving US-source income from Roblox. You'll need ONE of:

| Form | Use case | When to pick this |
|---|---|---|
| **W-8BEN** (Individual) | You're paid as an individual person. Income flows to your personal tax return. | Pick this if you're starting solo, no SA company registered, simplest path. |
| **W-8BEN-E** (Entity) | You've registered an SA company (Pty Ltd), and Roblox payouts go to the company. | Pick this if you've already incorporated OR plan to in the next 12 months. |

**Recommendation:** start with W-8BEN (individual) for the v1 validation phase. If/when revenue scales and you incorporate (likely month 9-12), update to W-8BEN-E. Roblox lets you replace the form on file.

### Step 4 — Get your South African Tax Number

If you don't already have one:
- Register on SARS eFiling at sarsefiling.co.za
- This is your South African Tax Reference Number (10 digits)
- You'll need this for the W-8BEN's "Foreign tax identifying number" field
- If you're an SA citizen and over 18, you almost certainly already have one — check your last IRP5 from any past employer

### Step 5 — Fill in the W-8BEN form

Roblox provides this through their tax-form workflow. Path:
- roblox.com/account/settings → "Payments" → "DevEx" → "Submit Tax Documents"
- Roblox uses TaxBandits or similar service to e-collect
- Fields you'll fill:
  - **Part I, Line 1:** Your full legal name
  - **Part I, Line 2:** Country of citizenship → South Africa
  - **Part I, Line 3:** Permanent residence address (your SA street address)
  - **Part I, Line 5:** US Taxpayer Identification Number (ITIN/SSN) — **leave blank** (you're not a US person)
  - **Part I, Line 6a:** Foreign tax identifying number → your SARS tax number from Step 4
  - **Part II, Line 9:** Treaty country → South Africa
  - **Part II, Line 10:** Article and paragraph of treaty → "Article 12, Paragraph 2" (royalty income, US-SA tax treaty)
  - **Part II, Line 10:** Withholding rate → "0%" (US-SA treaty rate for software royalties)
  - **Part III:** Sign + date
- Submit. Roblox processes in 5-15 business days.

**Why 0% withholding matters:** Without the W-8BEN, Roblox withholds 30% of every payout for US tax. With it, the SA-US tax treaty drops that to 0% for software/royalty income. Substantial difference at scale.

### Step 6 — Open or confirm a USD-receiving bank account

DevEx pays in USD via wire transfer or via Tipalti (Roblox's payment processor). Options:

- **Standard Bank / FNB / Nedbank international account** — established, supports USD wire receipt, FICA-compliant. Highest fees.
- **TymeBank / Capitec / Discovery Bank** — newer SA banks; USD wire support varies. Cheaper FX but may have lower limits.
- **Wise (formerly TransferWise) Multi-Currency Account** — widely used by SA freelancers. USD virtual account number; converts to ZAR at mid-market rate. Lowest fees by far. **Recommended for v1 / pre-incorporation phase.**
- **Mercury / Brex / similar US business banks** — only viable if you incorporate in the US, which is overkill for v1.

**Recommendation:** open a Wise account (~30 min, ~R200 setup), get a USD virtual account number, paste those bank details into Roblox's DevEx payment setup. Convert USD → ZAR via Wise as needed at mid-market rates.

### Step 7 — Submit DevEx application

After steps 1-6 are complete:
- roblox.com/account/settings → "DevEx" → "Apply"
- Roblox reviews the application (typically 5-10 business days)
- They confirm: Premium active ✓, Verified ✓, Tax form on file ✓, Bank account valid ✓, account in good standing ✓
- Approval = green light to receive DevEx payouts. No revenue yet, but you're cleared for the moment Robux start flowing.

---

## Logging your progress

Make a file: `~/Desktop/Founder-Mode-Validation-Kit/devex-progress.md`

```markdown
# DevEx + W-8BEN Progress

| Step | Status | Date completed | Notes |
|------|--------|----------------|-------|
| 1. Roblox Premium active | ☐ | | |
| 2. Identity verified (Persona) | ☐ | | |
| 3. Tax form chosen (W-8BEN / W-8BEN-E) | ☐ | | |
| 4. SARS tax number confirmed | ☐ | | |
| 5. W-8BEN submitted | ☐ | | Confirmation #: |
| 6. Wise USD account opened | ☐ | | Account #: |
| 7. DevEx application submitted | ☐ | | |
| 7a. DevEx approved | ☐ | | |
```

---

## Pitfalls

- **Don't skip the W-8BEN.** 30% withholding vs 0% is a material difference. The form takes 30 minutes and saves thousands of USD over a year of payouts.
- **Don't claim US residency by mistake** on Form W-8BEN. SA residents fill the foreign-person form, NOT W-9 (which is for US persons). Wrong form = withholding chaos.
- **Don't use a personal SA bank account for first DevEx** if you can use Wise. The FX cost difference between Wise (~0.5%) and a traditional SA bank (~3-6%) compounds significantly at $1k+ monthly.
- **Don't wait until your first 50k Robux to start.** That's the moment you'll wish you started 6 weeks earlier. Submit paperwork while there's no revenue pressure.
- **Don't forget to update the tax form** if you incorporate later. W-8BEN (individual) → W-8BEN-E (entity) requires resubmission. Roblox doesn't auto-migrate.
- **Don't forget treaty rate citation.** "Article 12, Paragraph 2" of the US-SA Income Tax Treaty (1997) is the legal basis for 0% withholding on software royalty income. Cite it explicitly on the form.
