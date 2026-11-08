# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|----------------|
| **Provider** | MindBridge's prototype is built and published through Lovable, and generation depends on the primary AI provider stack behind that experience. No second live provider is configured today. | H | Freeze new feature work, export prompts and sample outputs, route core generation to a backup provider behind the abstraction layer, and run the golden eval set before reopening traffic. |
| **Abstraction** | The product logic, output formats, and learner profile concepts are documented, but provider-specific generation behavior is not fully abstracted in the prototype. | M | Move prompts, output schemas, and format templates into provider-neutral files. Keep model name, endpoint, and safety settings in one config switch. |
| **Routing** | All generation uses the default path. There is no automatic failover if the primary provider is down, degraded, or repriced. | H | Turn on manual routing to a secondary provider for Plain Steps and Practice first. If generation is down, fall back to saved learner materials, cached adaptations, and template-based study sheets. |
| **Eval** | Class 1 kill criteria and sample lesson checks exist, but there is no automated eval harness that can prove a replacement provider is safe before a switch. | M | Build a 25-item golden set from real class material and learner corrections. Require a pass on factual accuracy, key omissions, reading level, and format match before any provider switch. |

## Portability Score
Partial. Prompts, product logic, output formats, learner profile schema, and eval criteria are portable. Hosting, authentication, stored learner data, and provider-specific generation behavior are not yet one-click portable.

## If primary AI provider doubles pricing tomorrow:
MindBridge would protect margin and continuity in the first 48 hours by turning on per-learner usage caps, caching repeated adaptations of the same source material, routing low-risk formats to a lower-cost model, and keeping higher-risk factual lessons on the stronger model. It would pause nonessential generation, tell pilot users plainly if session limits change, and start migration if the new unit cost breaks the margin model. The point of the kill switch is that price shock becomes an operations problem, not a shutdown.

## If primary AI provider ships a competing product:
The defensible asset is not generic AI generation. It is the accumulated MindBridge evidence layer: the learner profile, preference history, correction history, misconception map, course and assignment context, teacher-aligned practice, family and learner trust, and measured concept gains for neurodivergent learners. A provider can copy summarization, read-aloud, and quiz generation. It cannot instantly copy consent-based learner evidence, the correction patterns that improved outcomes, or the trust MindBridge earns by proving that its adaptations help learners finish and understand hard material.
