# AI Product Strategy: MindBridge

MindBridge is an AI learning companion for neurodivergent learners. It ingests lectures, slides, readings, videos, and assignments, then rebuilds the material into plain-language explanations, step-by-step breakdowns, stories, visuals, practice questions, checklists, and one-page study guides matched to how each learner processes information.

## Component 1: The Bet

Bet: We believe AI that converts class material into learner-matched formats changes neurodivergent learners from passive rereading and shutdown to active completion, so they understand difficult concepts faster and perform better in class.

Confidence: Medium

Kill criteria: Stop or pivot if a 3-week pilot with 20 target learners shows low completion, no comprehension gain over the original material, or unacceptable factual errors or omissions in adapted outputs.

## Component 2: The Moat

Data flywheel score: 15/20. Correction and Preference are the strongest loops because MindBridge is designed to reuse learner corrections and format preferences instead of starting blank each session. The weakest loop is Domain Context at 2/5: learning patterns can transfer across subjects, but subject mastery mostly stays local to the course.

Kill switch: Portability is Partial. Prompts, product logic, output formats, learner profile schema, and eval criteria are portable. Hosting, authentication, stored learner data, and provider-specific generation behavior still need abstraction and a tested backup route.

## Files

- 01-the-bet/diagnostic.md
- 01-the-bet/prototype.md
- 02-the-moat/data-flywheel.md
- 02-the-moat/kill-switch.md
