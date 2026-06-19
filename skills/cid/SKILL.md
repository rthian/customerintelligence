---
name: cid
description: Generalized Competitor Intelligence Database for any industry (SaaS, retail, telco, healthcare, FMCG, B2B services, fintech-non-bank, etc.). Builds a massive, foundational competitor action database from scratch using a universal Tier-1 taxonomy + pluggable Tier-2 industry overlay, multi-source signal pack (sentiment CSV + reviews + Glassdoor + tickets + transcripts), positioning/moat synthesis, and industry-aware 12-quarter forecasting. Use when the user wants exhaustive competitive intelligence outside banking. For banking/fintech-bank use the `cid-bank` skill instead.
origin: customer-intelligence
---

# CID — Competitor Intelligence Database (Generalized)

Act as an expert **Market Researcher and Competitive Intelligence Agent**. The strict objective is to build a massive, foundational Competitor Intelligence Database from scratch — monitoring every distinct campaign, product release, pricing change, channel move, service update, and corporate action for a specific competitor over a multi-year historical period, in any industry.

## When to Activate

- User wants competitive intelligence on a non-bank competitor (SaaS, retail, telco, healthcare, FMCG, B2B services, marketplace, consumer brand, etc.)
- User provides a Focal Competitor + Industry + Market + Time Period
- User wants to reverse-engineer campaigns from a customer signal pack (sentiment CSV, reviews, ticket export, etc.)
- User wants positioning/moat synthesis and forward quarterly forecasts
- User mentions "competitor intelligence", "CI database", "deep competitive sweep", or similar
- For banks / fintech-banks → use `cid-bank` instead

## Strict Database Constraints (Universal)

### No Summarization or Collapsing
- Do NOT group, summarize, or collapse distinct moves
- Every distinct release, promo, price change, partnership, hire, or filing MUST have its own row
- Prioritize extreme exhaustiveness

### Preserve Exact Language (No Sanitization)
- Do NOT corporatize messaging
- Capture the exact campaign names, product nicknames, pricing labels, hashtags, and prize mechanics
- Quote slogans verbatim; preserve original-language phrasing with translation in parentheses

### No Hallucinations
- If exact dates are unclear: `Approximate based on source.`
- Every row must have a real source — never fabricate
- Do NOT truncate

## Category — Two-Tier System

### Tier 1: Universal Action Layer (always applied)

| Tier 1 Category | Definition |
|---|---|
| **Product / Offering** | Anything a customer buys, signs up for, or uses (new SKU, new plan, new feature, new service line) |
| **Pricing** | List price, promo, rebate, bundle, tier change, discount mechanic |
| **Promotion / Campaign** | Marketing pushes, prize draws, partnerships, sponsored content, ad creatives |
| **Channel / Distribution** | New geos, retailers, integrations, marketplaces, sales motions, partner ecosystem |
| **Service / Support** | SLAs, warranty, onboarding flows, customer success programs, support hours |
| **Brand / Communications** | Rebrand, brand campaign, sponsorship, PR moment, founder visibility |
| **Digital / UX** | App release, web update, AI feature, self-serve UX, accessibility, performance |
| **Talent / Org** | Leadership change, restructure, layoffs, hiring waves, key departures |
| **Capital / Corporate** | Funding round, M&A, debt issuance, dividend, buyback, governance change, ESOP refresh |
| **Regulatory / Compliance** | Licenses won/lost, settlements, certifications, lawsuits, policy enforcement |

### Tier 2: Industry Overlay (loaded on declaration)

The user declares industry at Step 0. Use one of the overlays below to refine `Product / Offering`, `Pricing`, and `Channel` rows. If industry is unlisted, propose a Tier 2 overlay and confirm with user before proceeding.

**SaaS / B2B Software**
- Free Tier / Self-Serve / PLG
- SMB Plan / Mid-Market Plan / Enterprise
- Add-on / Module / Marketplace App
- API / Developer Platform / SDK
- Integration / Partner App / OEM
- Usage Metering / Seat Pricing / Consumption Pricing

**Retail / Consumer Goods**
- Hero SKU / SKU Refresh / SKU Discontinuation
- Category Expansion / Sub-brand
- Bundle / Multi-buy / Promo Pack
- Loyalty Program / Tier / Rewards Currency
- Store Format / Pop-up / Flagship
- D2C / Marketplace / Wholesale / Retail Partner

**Telco**
- Postpaid Plan / Prepaid Plan
- Fiber / Mobile / Roaming / Enterprise Connectivity
- Device Bundle / Trade-in
- Family Plan / Add-on Pack
- Convergence Bundle (mobile + fiber + TV)

**Healthcare / Pharma**
- Drug / Indication / Label Expansion
- Trial Phase / Readout
- Regulatory Approval / Filing
- Reimbursement / Payer Coverage
- Provider Network / Channel Partner
- Patient Support Program

**FMCG / Food & Beverage**
- Hero SKU / Limited Edition / Seasonal
- Pack Size / Format / Multipack
- Distribution Channel (modern trade / general trade / e-commerce / HORECA)
- Trade Promo / Consumer Promo
- Sub-brand / Brand Extension

**B2B Services / Consulting / Agencies**
- Practice / Vertical / Specialty
- Methodology / Framework / Productized Service
- Pricing Model (fixed-fee / retainer / outcome-based)
- Geographic Office / Region
- Industry Solution / Bundle

**Marketplaces / Platforms**
- Supply Side (seller, host, driver, creator) initiatives
- Demand Side (buyer, guest, rider, viewer) initiatives
- Take Rate / Fee Structure
- Trust & Safety / Verification
- Cross-side Network Mechanic

**Consumer Apps / Subscription**
- Free / Trial / Tier / Annual Plan
- Content Drop / Catalog Update
- Engagement Mechanic / Streak / Gamification
- Monetization Toggle (ads, IAP, subscription)

If the focal competitor spans multiple industries, declare a primary overlay and note hybrid rows in the mechanics column.

## Action Classification (Universal)

Tag each row in its OWN dedicated column as exactly one of:

- **[Market Action]** — Customer-facing moves (product, pricing, promo, channel, service, brand, digital)
- **[Corporate Action]** — Backend engine moves (funding, M&A, debt, dividends, governance, ESOP, board)
- **[Digital/SLA Action]** — Operational/UX/SLA updates (app release, eKYC, response-time changes, status incidents)
- **[Talent Action]** — Org/people moves (leadership, layoffs, hiring waves, key departures)
- **[Regulatory Action]** — Licenses, settlements, certifications, enforcement

### The Customer-Facing Test
Before classifying, ask: *"Can a customer (retail, business, developer, patient, partner — whichever applies) sign up for, use, or receive this specific item?"*
- YES → likely `[Market Action]` or `[Digital/SLA Action]`
- NO → must be `[Corporate Action]`, `[Talent Action]`, or `[Regulatory Action]`

## Standard Output Format

| (1) Tier 1 Category | (2) Tier 2 Sub-Category | (3) Action Classification | (4) Exact Campaign / Release Name | (5) Specific Mechanics / Features | (6) Exact Period / Dates | (7) Confidence | (8) Source / Evidence |
|---|---|---|---|---|---|---|---|

**Confidence column:**
- `High` — primary source, exact date, verbatim language
- `Medium` — secondary source, dates inferred from publication, paraphrased language
- `Low` — single ambiguous mention, requires triangulation
- `Approximate` — date or detail explicitly approximated

EVERY row in EVERY part must follow this 8-column format.

---

## Step 0: Project Setup (BEFORE Part 1)

Ask the user to confirm:

1. **Primary Focal Competitor** — the deep-dive target
2. **Adjacent Competitor Set** — 2 to 4 names for relative positioning (optional but recommended)
3. **Industry / Vertical** — to load Tier 2 overlay
4. **Geography / Market** — drives regulatory and local-source pivots
5. **Time Period** — start year → end year
6. **Strategic Question** — *"Why are we doing this?"* (e.g., entry decision, defense plan, pricing reset, M&A target screen, fundraising deck)
7. **Available Signal Sources for Part 2** — pick all that apply:
   - Sentiment CSV (social listening export)
   - App Store / Play Store reviews
   - Trustpilot / G2 / Capterra reviews
   - Glassdoor employee reviews
   - Support ticket export
   - Sales call transcript bundle
   - Press / news mention export
   - Other (specify)
8. **Public vs. Private Status of Focal Competitor** — informs Layer 3 source pivot

If the focal competitor is **private / early-stage**, Layer 3 will pivot from regulatory filings to: LinkedIn hiring patterns, job posts, founder podcasts/interviews, fundraise rumors, partnership announcements, investor portfolio pages, patent filings.

Confirm Step 0 outputs back to the user before proceeding.

---

## Workflow Strategy — 5 Distinct Parts

Execute in 5 parts. **Do NOT move to the next part until the user explicitly gives the command.**

(Banking version has 4 parts; this version inserts Part 3.5 → Positioning & Moat Synthesis.)

---

## Part 1: Triple-Sweep Intelligence Gathering (Year-by-Year)

### Step 1: Confirm Step 0 inputs
Re-state competitor, industry, geography, time period, strategic question.

### Step 2: Year-by-year execution (anti-truncation)
Execute the Triple-Sweep for the **FIRST YEAR ONLY** of the time period.

**Layer 1: Market & Competitive Action**
- Wayback Machine archives of website, T&Cs, pricing page, product page
- Ad transparency libraries (Meta Ad Library, Google Ads Transparency, TikTok Creative Center, LinkedIn Ad Library)
- Social platforms (Facebook, Instagram, TikTok, X/Twitter, Threads, LinkedIn, YouTube)
- Community / forum platforms (Reddit, niche forums, Discord, Slack communities, industry Slacks)
- Review sites (G2, Capterra, Trustpilot, App Store, Play Store, Yelp, Trustradius, Glassdoor)
- Industry press, trade publications, niche newsletters
- Goal: capture exact mechanics of campaigns, releases, partnerships

**Layer 2: Product & Digital**
- App Store / Play Store release notes
- GitHub releases, public changelogs, status page incidents
- Public docs version history (use Wayback diff)
- Product Hunt launches
- Webinar / event announcements
- Pricing page Wayback diffs
- Goal: track feature velocity and pricing-page micro-moves

**Layer 3: Capital & Governance**

For **public companies:**
- SEC EDGAR (or local equivalent: BNM, MAS, ASIC, FSA, etc.) — 10-K, 10-Q, 8-K, S-1, proxy statements
- Earnings calls / transcripts (Seeking Alpha, investor relations pages)
- Analyst reports
- Credit rating reports
- Insider trading filings (Form 4)

For **private companies:**
- Crunchbase / PitchBook / CB Insights signals
- LinkedIn hiring trends and headcount growth
- Job posts (signal: which roles hint at strategy)
- Founder/exec podcast appearances and interviews
- Fundraise rumors (The Information, TechCrunch, Axios)
- Partnership announcements
- Patent filings (USPTO, EPO, WIPO)
- Investor portfolio pages

For **all companies:**
- Court filings, regulatory enforcement actions
- M&A databases
- News alerts on the company name

### Exhaustive Sweep Rule
Conduct Layer 1, then Layer 2, then Layer 3 — combine into one table for the year before showing the user.

### Step 3: Extract & format
For every finding extract:
- Tier 1 Category + Tier 2 Sub-Category
- Action Classification
- Exact name (verbatim)
- Mechanics or features
- Precise dates
- Confidence level
- Source

Format into the 8-column Standard Output Format Markdown table for that specific year.

### Step 4: Stop and prompt
Stop and ask: *"Proceed to the next year?"*

Repeat Steps 2 & 3 chronologically until the entire multi-year period is complete.

### Step 5: Deeper sweep offer
After the final year: *"Want me to do a deeper sweep in case anything is missed before consolidating?"*

### Step 6: Consolidation
Combine all yearly data into ONE combined Markdown table for export.

### Step 7: Hand-off
Stop and ask the user to upload the **signal pack** for Part 2 (any combination of CSV, review exports, ticket exports, transcript bundles).

---

## Part 2: Multi-Source Signal Pack & Spike Analysis (Reverse-Engineering)

The Quiet + Loud + Forensics logic applies to **whichever signals exist**. If multiple signal types are uploaded, run the analysis on each separately, then merge findings into one Part 2 table.

### Step 1: Baseline Audit & Keyword Sweep (Steady-State Detection)

Analyze each uploaded signal source in its **entirety**.

**Anti-truncation requirement:** Explicitly state, per source:
- Total row count identified
- Total rows processed
- Any rows skipped and why

**The Keyword Library:** Build an exhaustive list of keywords for the focal entity:
- Company name (full + abbreviations + parent + sub-brands)
- Product/feature/SKU names + nicknames
- Common misspellings
- Unique hashtags / campaign tags
- Founder / CEO names (often surface in product mentions)
- Competitor mentions (when users compare in reviews)

Use these to systematically crawl every signal source.

**The "Quiet" Extraction:** Identify products, features, or service traits mentioned consistently over time **without** spikes. Captures always-on mechanics, baseline product reality, and structural pain points.

### Step 2: Chronological Spike Analysis (Event Detection)

**Frequency Mapping:** Per source, perform chronological volume analysis to isolate "Volume Anomalies" (Spikes). Identify date ranges where mentions or specific keywords deviate significantly from baseline.

**The "Loud" Extraction:** Isolate spikes as indicators of:
- High-impact launches or campaigns
- Grand prize / major incentive announcements
- Sudden systemic outages or service failures
- PR crises or viral moments
- Pricing changes that triggered backlash
- Layoffs or leadership departures (if signal type covers it)

### Step 3: Contextual Forensics & Reverse-Engineering

Treat findings from Sweep + Spike as "Signals." For each signal, analyze surrounding text to reconstruct:

- **Incentive & Barrier:** What was offered + what the user had to do (e.g., "Sign up for annual plan to unlock $200 credit")
- **Shadow Mechanics:** Referral codes, hidden links, partner platforms, unannounced collaborations
- **Grassroots Flavor:** Capture unsanitized language verbatim. Non-English → preserve original + translation in parentheses
- **Sentiment Polarity:** Tag positive / negative / mixed for the spike — distinguishes a launch hit from a service crisis
- **Persona Cues:** When obvious from context, note who is talking (existing customer, prospect, competitor employee, partner, journalist)

### Step 4: Produce table(s)

Produce a SEPARATE table per signal source, OR one merged Part 2 table with a `Signal Source` column appended.

EVERY row follows the 8-column Standard Output Format + Action Classification.

### Step 5: Hand-off

Stop and ask: *"Should I merge the data for Part 3?"*

---

## Part 3: Data Merger and Overlap Analysis

### Step 1: Combine & deduplicate
- Combine tables from Part 1 and Part 2
- Remove EXACT duplicates only
- Keep distinct variations as separate rows
- Present the **Final Master Table**

### Step 2: Overlap Analysis (Analyst Insight)

Below the master table, provide an Analyst Insight section explaining:
- What "official" data Part 1 caught that the public ignored or never amplified
- What "hidden" grassroots campaigns/issues Part 2 caught that the official channels suppressed
- Cross-source patterns (e.g., a launch that crushed it on App Store reviews but was invisible on Glassdoor → product win, internally painful)
- Source-credibility weighting (e.g., Glassdoor "talent action" leading indicators predict layoffs in filings 2 quarters later)

### Step 3: Hand-off
Stop and ask: *"Is the data sufficiently extensive before proceeding to Part 3.5?"*

---

## Part 3.5: Positioning, Moat & Whitespace Synthesis (NEW)

This is the meta-layer that interprets the database.

### Step 1: Positioning Shift Map
Plot how the focal competitor's messaging changed over the time period:
- Year-over-year tagline / brand promise
- Target customer shifts (SMB → Enterprise, mass → premium, etc.)
- Category framing shifts ("we are X" → "we are Y")

### Step 2: Moat Assessment
Evaluate each moat dimension based on the database:
- **Pricing power** — frequency of price increases without churn signals
- **Distribution lock-in** — exclusive partnerships, owned channels
- **Network effects** — supply/demand growth signals
- **Switching costs** — data lock-in, integration depth, contract length
- **Regulatory moat** — licenses, certifications, compliance head-start
- **Talent moat** — concentration of senior hires, key retention signals
- **Capital moat** — runway, unit economics if observable

Score each moat as `Strong / Moderate / Weak / Eroding` with evidence rows referenced.

### Step 3: Whitespace Map
Identify where the focal competitor did **nothing**:
- Tier 1 categories with zero or minimal activity
- Tier 2 sub-categories untouched
- Geographies skipped
- Customer segments ignored
- Adjacent product extensions not pursued

Whitespace is often the most strategic insight — it tells the user where to attack or where the competitor is structurally constrained.

### Step 4: Hand-off
Stop and ask: *"Ready to proceed to Part 4 forecasting?"*

---

## Part 4: Strategic Framework Analysis and Forecasting

### Step 1: Apply frameworks
Draw on industry-appropriate frameworks:
- **All industries:** SWOT, Porter's Five Forces, Wardley Maps
- **SaaS:** Crossing the Chasm, PLG vs. Sales-Led, Rule of 40
- **Retail:** Seasonal calendar, category captaincy, private-label cycles
- **Healthcare:** Trial phase gates, label-expansion patterns, payer-mix shifts
- **B2B Services:** Practice maturity curve, vertical penetration sequences
- **Telco:** Capex cycle, spectrum cycle, convergence bundling

### Step 2: 12-quarter forecast (HARD REQUIREMENT)

You MUST provide **EXACTLY 12 distinct entries** — one per quarter for the next 3 years.

Each entry follows the 8-column Standard Output Format and ties forecasts to industry-specific drivers:

| Industry | Primary Forecast Driver |
|---|---|
| SaaS | ARR cycle, fundraise runway, hiring waves, pricing experiments |
| Retail | Seasonal calendar, SKU drops, margin pressure, store openings |
| Healthcare | Trial readouts, approval calendar, label expansions, payer cycles |
| Telco | Capex cycle, spectrum auctions, regulatory windows, convergence pushes |
| FMCG | Trade calendar, innovation pipeline, channel mix shifts |
| B2B Services | Sales-cycle compression, vertical pivots, methodology launches |
| Marketplace | Take-rate cycles, supply/demand balance interventions |
| Consumer App | Content drops, monetization toggles, growth-loop experiments |

Each forecast row must include:
- Predicted Tier 1 + Tier 2 category
- Predicted action classification
- Hypothesized name / mechanic
- Quarter (Q#-YYYY)
- Confidence (High / Medium / Low)
- Justifying evidence rows from Parts 1–3.5

### Step 3: Final hand-off
Once Part 4 is complete: *"Want me to create a Markdown file report you can copy-paste into Google Docs or Notion?"*

If yes — output the entire 5-part analysis as a single, copy-paste-ready Markdown file.

---

## Refresh Protocol (for repeat engagements)

If the user requests a refresh later:
- Do NOT re-run from year 1
- Run an **incremental sweep** from the last covered date forward
- Re-run Parts 2 → 3.5 → 4 with the appended data
- Flag changes in moat scores and whitespace map vs. prior run

## Quality Gate Before Each Part Hand-off

Before stopping and asking the user to proceed:

- [ ] Every row follows the 8-column Standard Output Format
- [ ] Every row has Tier 1 + Tier 2 + Action Classification
- [ ] Every row has a Confidence rating
- [ ] No moves have been collapsed or summarized
- [ ] Original campaign names, slogans, and mechanics preserved verbatim
- [ ] Mechanics column explains how a customer participates
- [ ] Dates are exact OR explicitly marked "Approximate based on source"
- [ ] Customer-Facing Test applied to every classification
- [ ] No fabricated entries — every row has a real source
- [ ] Public vs. private Layer 3 pivot applied correctly

## Anti-Patterns to Avoid

- ❌ Defaulting to banking categories when industry is SaaS / retail / etc.
- ❌ Skipping Step 0 and assuming industry from competitor name
- ❌ Using only one signal source in Part 2 when multiple were provided
- ❌ Skipping Part 3.5 — the positioning/moat layer is what makes this strategic, not just descriptive
- ❌ Producing fewer than 12 quarterly forecasts in Part 4
- ❌ Forecasting without grounding in evidence rows from earlier parts
- ❌ Hallucinating filings for private companies — pivot to LinkedIn / job posts / podcast Layer 3
- ❌ Sanitizing grassroots language or losing the original-language phrasing
- ❌ Re-running from year 1 on a refresh instead of incremental sweep
