# AI Product Strategy: MindBridge

MindBridge is an AI learning companion for neurodivergent learners. It ingests lectures, slides, readings, videos, and assignments, then rebuilds the material into plain-language explanations, step-by-step breakdowns, stories, visuals, practice questions, checklists, and one-page study guides matched to how each learner processes information.

## Component 1: The Bet

Bet: We believe AI that converts class material into learner-matched formats changes neurodivergent learners from passive rereading and shutdown to active completion, so they understand difficult concepts faster and perform better in class.

Confidence: Medium

Kill criteria: Stop or pivot if a 3-week pilot with 20 target learners shows low completion, no comprehension gain over the original material, or unacceptable factual errors or omissions in adapted outputs.

## Component 2: The Moat

Data flywheel score: 15/20. Correction and Preference are the strongest loops because MindBridge is designed to reuse learner corrections and format preferences instead of starting blank each session. The weakest loop is Domain Context at 2/5: learning patterns can transfer across subjects, but subject mastery mostly stays local to the course.

Kill switch: Portability is Partial. Prompts, product logic, output formats, learner profile schema, and eval criteria are portable. Hosting, authentication, stored learner data, and provider-specific generation behavior still need abstraction and a tested backup route.

## Component 3: The Margin

Cost curve: At a $24/month learner price, base AI COGS is $11.50 per active learner per month, for a 52.1% gross margin. The cost curve improves to 62.1% at 10,000 learners if cascading, source reuse, caching, and eval automation hold, but it can go negative if inference costs triple or heavy users are not priced into the right band.

Pricing model: Hybrid. A per-learner base price covers the profile, saved lessons, and standard volume, with Core and Intensive usage bands for school contracts so intensive learners are not silently subsidized by light users.

## Component 4: The Contract

Reliability contract: MindBridge promises source-grounded learning help, not confident guessing. Targets are at least 92% source-supported claims, fewer than 2% of lessons with an unsupported material claim, standard lesson latency under 45 seconds at p95, and drift held within 2 points week over week without an approved change.

Golden dataset: The spec starts with 10 rows covering core adaptation, practice correction, exact numbers, messy source material, prompt injection, privacy, high-risk health content, and learner corrections. Production target before a paid pilot is 150 golden rows.

## Files

- 01-the-bet/diagnostic.md
- 01-the-bet/prototype.md
- 02-the-moat/data-flywheel.md
- 02-the-moat/kill-switch.md
- 03-the-margin/cost-curve.md
- 04-the-contract/golden-dataset.md
