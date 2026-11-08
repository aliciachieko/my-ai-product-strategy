# Cost Curve & Pricing Strategy

Planning model for the MindBridge course product. These are stated assumptions for the exercise, not vendor quotes.

**Base learner assumption:** One active learner uses MindBridge for 12 adapted lessons per month, 40 practice checks, 6 audio listens, 3 visual maps, and 8 remakes or follow-up explanations. The pricing test uses a direct learner price of $24/month.

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $5.90 | Frontier model work for dense source material, low-confidence outputs, persistent misconceptions, and final quality passes on higher-risk lessons. |
| Inference (cascading/triage) | $1.35 | Low-cost model work for chunking, first-pass plain language rewrites, flashcards, simple practice, format conversion, and confidence scoring. |
| Infrastructure | $1.10 | App hosting, backend compute, monitoring, error tracking, and delivery infrastructure allocated per active learner. |
| Data/storage | $0.85 | Upload storage, embeddings, retrieval search, learner profile storage, saved lessons, and backups. |
| Human-in-the-loop | $2.30 | Sampled educator review, factual spot checks, support escalations, and review of flagged lessons, allocated per active learner. |
| **Total AI COGS** | **$11.50** | At $24/month, gross profit is $12.50 per learner and gross margin is 52.1% before salaries, sales, and general overhead. |

## Cost Curve

| Scale | AI COGS per active learner | Gross margin at $24/month | What changes |
|------|---------------------------|---------------------------|--------------|
| 100 learners | $14.60 | 39.2% | Low cache reuse, too much frontier model use, manual review, and fixed infrastructure spread across too few learners. |
| 1,000 learners | $11.50 | 52.1% | Base case. Cascading, templates, and sampled review are working, but heavy users still need active management. |
| 10,000 learners | $9.10 | 62.1% | Better source reuse, higher cache hit rate, stronger routing rules, volume pricing, and more automated eval coverage. |
| 100,000 learners | $7.85 | 67.3% | The curve flattens. Tokens, audio, storage, and trust and safety checks remain variable, so usage never becomes free. |

The curve improves with scale only if MindBridge reuses prior work. If every upload starts from zero and every remake goes to the frontier model, scale makes the cost problem bigger instead of smaller.

## Cascading Strategy

**Triage model:** A low-cost model handles classification, chunking, reading-level rewrites, flashcards, first-pass practice questions, simple format conversion, and confidence scoring.
**Frontier model:** A high-capability model handles dense academic text, tables, multi-step reasoning, low-confidence triage output, repeated learner corrections, sensitive topics, and final passes where factual error would damage trust.
**Routing rule:** Start cheap, escalate only when the work needs it. Escalate if triage confidence is below 0.80, the source includes dense concepts or structured data, the learner has already corrected the output once, practice answers show the misconception is still present, or the topic is medical, legal, safety, or otherwise high risk.
**Expected cascade ratio:** About 75% of generation stays on the low-cost path and 25% escalates to the frontier model. By spend, the split is closer to 55% low-cost and 45% frontier because frontier calls are longer and more complex.

## Pricing Model

**Current pricing:** MindBridge is still a course prototype, so there is no live price. The comparison point is a traditional study app at about $12/month with very low marginal delivery cost.
**Proposed AI pricing:** $24/month per learner for direct purchase. School contracts are priced per active learner using the same cost model, with Core and Intensive bands set before enrollment based on expected lesson volume, audio and visual use, and human review needs.
**Model:** Hybrid. The base seat price covers the learner profile, saved lessons, standard lesson volume, and all core formats. Usage bands protect margin for intensive learners instead of letting light users silently subsidize the heaviest users.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Inference rises from $7.25 to $21.75 per learner. Total AI COGS rises to $26.00, gross profit falls to -$2.00, and gross margin falls to -8.3%. | Tighten routing the same day: frontier model only for low confidence, high risk, or failed correction cases. Cache repeated adaptations of the same source, compress context, cap nonessential remakes, route eligible work to a backup provider, and pause free generation until unit cost is back under the price floor. |
| Heaviest segment doubles | The top 10% of learners run at about 3.2x average cost. If that cohort doubles its use, blended AI COGS rises by about $3.68 to $15.18 per learner. Gross margin falls from 52.1% to 36.8%. | Move intensive learners into the correct pricing band, add fair-use limits for audio and visual generation, encourage saved lesson reuse instead of regeneration, batch non-urgent processing, and review the cohort weekly so a small group does not quietly consume the margin. |
| Model provider raises prices 50% | Inference rises from $7.25 to $10.88 per learner. Total AI COGS rises to $15.13, gross profit falls to $8.87, and gross margin falls to 37.0%. | Use the kill switch plan: shift eligible traffic to the backup provider after it passes the golden eval set, raise the cascade ratio, renegotiate or commit only after eval results are stable, and apply the new price floor to renewals and new school contracts. |

## Board One-Pager

**Before (traditional SaaS):** A flat $12/month study app can carry AI COGS and delivery cost near $1.20 per user per month, for gross margin near 90%. The economics look excellent because the product does less: static content, light personalization, and little evidence that the learner actually understood the material.
**After (AI-enabled):** MindBridge charges $24/month because the product does real work per learner: it reads source material, adapts it to the learner, remembers preferences and corrections, generates practice, and checks whether the learner is improving. At the base case, AI COGS is $11.50 and gross margin is 52.1%. With routing, reuse, and eval automation, margin can move into the low 60% range at scale. Without controls, the same product can go margin-negative under inference shock or heavy-user growth.
**Net margin shift:** Gross margin drops by about 38 points versus traditional SaaS, from about 90% to 52.1%, in exchange for personalization, correction memory, and measured learning outcomes. The strategy is to defend a workable AI margin: stay above 50% in the base case, push toward 60% through cascading and reuse, and price intensive use honestly instead of pretending AI usage is free.
