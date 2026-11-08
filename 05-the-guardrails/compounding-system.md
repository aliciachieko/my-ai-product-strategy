# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Learner correction loop | Corrections, "too hard" or "too easy" flags, remake requests, failed formats | Updated learner profile, prompt rules, and new golden dataset rows so the same failure is tested forever | Y | active in design, broken in the current prototype across sessions |
| Preference loop | Format choices, reading level, audio use, pace, session length | Defaults that start each new lesson the way this learner learns best | Y | active in design, partial in the prototype |
| Practice outcome loop | Practice answers, hint use, misconception patterns | Mastery map that changes what the next lesson explains first and what it skips | Y | active |
| Educator review loop | Educator approvals, edits, and rejections on flagged lessons | Reviewer decisions written back into the golden dataset, routing rules, and prompt rules | Y | missing in the direct learner product, required in school deployments |
| Cross-course transfer loop | Reasoning patterns and misconception types tagged in one course | Better first-pass lessons in an adjacent course, without moving subject facts across courses | Y, limited | broken by design tension: course scoping prevents contamination and also blocks transfer |

**Broken loop identified by partner:** The learner correction loop. In the current prototype, a correction improves the lesson in front of the learner and then disappears when the session ends. That is the exact failure the data flywheel warns about: the signal does not compound, so the learner has to teach MindBridge the same lesson again next time.
**Fix plan:** Ship a persistent, consent-based learner profile before any paid pilot. Corrections are stored against concepts, not just chats; the learner can see, edit, and delete what is saved; every stored correction creates or updates a golden dataset row; and the first screen of a new session shows what MindBridge remembered. Success measure: repeat corrections on the same concept fall by at least half within one term.

## Context Connectivity

The learner profile is the hub. It holds preferences, correction history, and the mastery map, and every part of the product reads from it. Course namespaces hold subject facts, misconceptions, and practice history, and they stay separate on purpose, so sociology facts never leak into a chemistry lesson. A thin transfer layer holds only tagged reasoning patterns and misconception types, which are allowed to move across courses. Educators in a school deployment see aggregate misconception trends for their class, not a learner's raw work, unless the learner shares it. The product team sees de-identified correction clusters weekly, which is how repeated failures become eval cases and routing rules.

Where it silos: facts silo by course, which is a safety feature with a transfer cost. Learner data silos away from generation services, which receive only the source material and format settings they need, not the full profile. The real connectivity gap is the educator view: a teacher cannot see why a learner keeps missing a concept unless the learner shares a report. The fix is a learner-controlled share report, generated from the mastery map, that the learner sends to a teacher, tutor, or parent on purpose.

## Governance Policy

**Scope:** Every AI-generated adaptation, explanation, practice set, feedback message, and recommendation MindBridge produces, for learners, educators, and admins. Out of scope by design: MindBridge teaches and checks understanding. It does not write graded submissions for the learner, and it redirects requests to complete graded work verbatim into explanation and practice instead.
**Autonomy boundaries:** MindBridge may adapt material, explain, quiz, and give feedback on its own. It may not change or predict official grades, message teachers, parents, or schools, share one learner's data with anyone, make placement, eligibility, or accommodation decisions, or give medical or mental-health advice. Those actions are either refused, routed to a human, or left entirely to the school and family.
**Escalation triggers:** Low confidence under the Class 4 contract; the same concept corrected twice; an uploaded file that tries to redirect the AI; any request for another learner's data; a safety or self-harm disclosure, which routes to crisis resources and, in a school deployment, the school's own trusted-adult process; high-risk subject matter such as medication or legal rights; and any model or provider change, which cannot ship until the golden dataset passes again.
**Audit cadence:** Weekly golden dataset run against the reliability contract. Monthly access and data review: who and what touched learner data. Quarterly accessibility and outcome review across learner groups, checking that reading-level gains and correction rates do not split badly by subgroup. Quarterly review of the vendor and model change log. Annual external privacy review before renewing school deployments.
**Regulatory exposure (EU AI Act / other):** Primary exposure is student privacy law, not general AI law: FERPA for education records in US school deployments, COPPA if any learner is under 13, and state student privacy statutes. Accessibility law matters for procurement: WCAG and Section 508 conformance. Under the EU AI Act, AI used to determine access to education or to evaluate learning outcomes for official records is high-risk; MindBridge is built and sold as study support that does not grade, place, or determine access, which keeps it out of that category, and the autonomy boundaries above are what keep that classification honest. If a school ever asks MindBridge to feed official grades or placement, the classification changes and the deployment stops until high-risk obligations are met. GDPR applies if EU learners are served.

## Agent Topology

MindBridge runs five task agents with narrow permissions. The **Ingestion Agent** parses, OCRs, and chunks source material; it cannot generate claims, and it flags illegible or missing content instead of guessing. The **Adaptation Agent** generates the learner's chosen formats from the source and profile; it cannot introduce facts that are not in the source. The **Assessment Agent** builds practice and scores it against answer keys and the mastery map; it cannot assign or predict official grades. The **Profile Agent** stores preferences and corrections with consent; it cannot share data across learners or courses. The **Review Router** scores confidence and sends flagged lessons to a human; it cannot approve its own flagged output, and no agent can change another agent's permissions.

Human approvals: the learner approves anything saved to long-term memory and can delete it. An educator approves high-risk lessons before release in a managed school deployment. An admin approves any new use of learner data. A named product owner approves any model, provider, or prompt change after the golden dataset passes.

## Shadow AI Audit

Planning audit for a 100-learner pilot school environment: the unsanctioned AI tools already in use around MindBridge, triaged before launch.

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| Personal ChatGPT accounts used by students on class material | None (student-owned) | H | govern: offer MindBridge as the sanctioned path, teach what may not be pasted into personal accounts |
| Photomath and similar solvers used to complete homework | None (student-owned) | M | govern: allowed for checking work, not for graded submissions; MindBridge practice mode is the alternative |
| Copilot and Gemini features inside the school productivity suite | District IT | M | govern: align suite AI settings and data rules with the deployment agreement instead of fighting the default |
| Grammarly on student writing | Individual teachers | L | keep: writing mechanics help, no class data leaves the learner's own document |
| Notion AI used by the MindBridge product team for internal docs | Product operations | M | govern: internal docs only, never learner data, corrections, or uploads |

**Total tools found:** 5
**Tools after triage:** 5 (0 killed, 4 governed, 1 kept). Nothing is killed because bans students route around do not reduce risk; the sanctioned path and clear data rules do.
**Estimated hidden spend:** About $2,400 per year across the pilot in scattered personal subscriptions (roughly $20 per month for a handful of students, teachers, and team members), plus the unpriced cost: class material sitting in personal accounts outside any data agreement.
