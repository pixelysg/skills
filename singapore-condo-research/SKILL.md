---
name: singapore-condo-research
description: >-
  Research Singapore condo projects with grounded facts, URA transaction analysis,
  price trends, budget checks, and peer comparisons.
---

# singapore-condo-research

Use this skill when the user asks for condo project research in Singapore, such as:
- "deep dive on <condo name>"
- "tell me about <condo name>"
- "quick facts for <condo name>"
- "compare <condo A> vs <condo B>"
- "can I get a 3BR at <condo> for $X?"
- "price trend for <condo name>"

## 1. Quick Facts Lookup

For every condo query, start with a concise quick-facts summary:

- Project name
- Location / street
- District
- Tenure (99yr leasehold from YYYY / freehold) and remaining years
- Project type (private condo or EC; if EC, note MOP/privatisation status)
- TOP year
- Total units
- Unit mix by bedroom type with sqft ranges

### Data-source priority

1. **use-agently.com** agents (Jina, Exa Search) for initial grounding
2. **propertyguru.com** or **99.co** project detail pages
3. **stackedhomes.com** only when a relevant project article exists
4. Supplementary **web search** for missing fields, with citations

**Never hallucinate** unit mix, tenure, TOP year, or district. If a field cannot be confirmed, say "not found in available sources."

### Data confidence

Rate each lookup:
- **High** — multiple consistent sources
- **Medium** — one credible source
- **Low** — partial or incomplete fields

List any **missing fields** explicitly.

## 2. Transaction Analysis (when URA data is available)

When the user provides a URA dataset or asks for price/trend analysis:

### Price trends
- Median price and PSF by year for the target unit type
- YoY growth % to show momentum
- Flag when sample size is small (< 5 txns in a period)

### Floor-level breakdown
- Group transactions into low (01-05), mid (06-10), high (11-15), penthouse (16+)
- Show price range per band for the most recent year

### Budget feasibility
- State the user's budget clearly
- Calculate **budget hit rate** — % of recent transactions (last 12-18 months) within budget
- Note which floor levels or unit configurations are realistic at that price
- Use ✅ ⚠️ ❌ markers for quick scanning

## 3. Peer Comparison

When comparing projects or when context would help:

- Match on **same bedroom count AND similar sqft range** (like-for-like)
- Compare: median price, PSF, lease commencement, remaining tenure, TOP year
- Present as a compact summary (bullet list for chat platforms, table where supported)
- Note trade-offs (e.g. newer lease but smaller unit, cheaper PSF but older facilities)

## 4. Output format

Structure findings using these sections as needed (skip sections that don't apply):

- 📋 **Quick Facts** — project basics, tenure, unit mix
- 📈 **Price Trend** — for target unit type, by year
- 🏢 **Floor Breakdown** — prices by floor band (recent year)
- 💰 **Budget Check** — feasibility at stated budget
- 🔄 **Peer Comparison** — vs similar projects
- ⚠️ **Caveats** — small sample sizes, data gaps, EC-specific notes

Use emoji markers and keep it scannable. On platforms without table support (Telegram, WhatsApp), use bullet lists.

## 5. EC-specific notes

For Executive Condos:
- State MOP status (5-year mark from TOP)
- Note if privatised (10-year mark) — affects resale pool and pricing
- Flag citizenship/PR eligibility restrictions if pre-privatisation

## 6. Memory and preferences

Store user preferences (preferred format, comparison criteria, target areas, budget) in:
- `singapore-condo-research/memory/user-preferences.md`

Only store non-sensitive preference notes. No credentials or personal secrets.
