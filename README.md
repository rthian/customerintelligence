# CID Skill - Competitor Intelligence Database

Generalized Competitor Intelligence Database for any industry (SaaS, retail, telco, healthcare, FMCG, B2B services, fintech-non-bank, etc.).

## Features

- **Universal Coverage**: Works across any industry with pluggable Tier-2 overlays
- **Multi-Source Analysis**: Integrates sentiment CSV, reviews, Glassdoor, tickets, transcripts
- **Strategic Depth**: Positioning/moat synthesis and 12-quarter forecasting
- **5-Part Workflow**: Exhaustive intelligence gathering → Signal analysis → Data merger → Positioning synthesis → Forecasting

## Installation

### Direct Install
```bash
git clone https://github.com/rthian/customerintelligence.git
cd customerintelligence
mkdir -p ~/.claude/skills/cid
cp skills/cid/SKILL.md ~/.claude/skills/cid/SKILL.md
```


## Usage

In Claude Code, invoke the skill:
```
/cid
```

Or mention competitive intelligence needs and Claude will suggest the skill.

## When to Use

- Competitive intelligence on non-bank competitors
- Reverse-engineering campaigns from customer signals
- Positioning and moat analysis
- Forward quarterly forecasts
- Deep competitive sweeps across any industry

## Supported Industries

- SaaS / B2B Software
- Retail / Consumer Goods
- Telco
- Healthcare / Pharma
- FMCG / Food & Beverage
- B2B Services / Consulting
- Marketplaces / Platforms
- Consumer Apps / Subscription
- And more...

## For Banking/Fintech

Use the `cid-bank` skill instead for banking-specific intelligence.

## License

MIT
