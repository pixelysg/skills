---
name: singapore-condo-research
description: Research Singapore condo projects with grounded facts and optional URA dataset analysis.
---

# singapore-condo-research

Use this skill when the user asks for condo project research in Singapore, especially requests like:
- "deep dive on <condo name>"
- "help search for <condo name>"
- "tell me about <condo name>"
- "quick facts for <condo name>"
- "condo analysis for <condo name>"

## Primary job

Help users quickly look up and summarize factual condo project information:
- location
- district
- tenure (leasehold/freehold)
- project type (condo or EC)
- land parcel sale/launch start (if available)
- TOP year
- unit mix by bedroom type (1BR, 2BR, 3BR, 4BR, 5BR)

Always ground outputs in cited source data. If a field cannot be found, explicitly say "not found in available sources" instead of guessing.

## Data-source policy

Prioritize sources in this order:
1. use-agently.com results that pull from agents such as Jina and Exa Search
2. Direct condo detail pages from:
   - propertyguru.com
   - 99.co
3. stackedhomes.com only when a relevant project article exists
4. Supplementary web search for missing fields, with citations

Never hallucinate unit mix, tenure, TOP year, or district. Use only verifiable facts.

## Output requirements

For each condo project query:
1. Return a concise quick-facts table.
2. Include unit mix counts (if found), with source links.
3. Add a "Data confidence" note:
   - High: multiple consistent sources
   - Medium: one credible source
   - Low: partial/incomplete fields
4. Add "Missing fields" listing anything not confirmed.

## Optional URA-dataset mode

When the user provides a URA dataset:
- Ground project facts and analysis primarily on the URA data.
- If possible, add surrounding-project context (same district and/or similar TOP year), clearly labeled.
- Use URA-grounded evidence for recommendation requests.

## Memory and preference handling

When user preferences are explicit (for example: preferred table format, preferred comparable-project criteria, or required fields), store them in this folder for reuse:
- `singapore-condo-research/memory/user-preferences.md`

Only store non-sensitive preference notes. Do not store credentials or personal secrets.
