# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point: adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 5/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 5/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 2/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 3/5 |

### Correction Loop - 5/5
**What you capture today:** MindBridge treats remake requests, "too hard" and "too easy" flags, factual corrections, skipped explanations, hint requests, and practice answers as labeled correction signals. Each signal is stored with the source concept, the format used, the learner profile, and whether the revised output fixed the problem.
**How it compounds:** The next lesson for that learner starts from the corrected pattern instead of repeating the failed one. Across learners, repeated corrections become an eval set and generation rules: which explanations create errors, which formats resolve a misconception, and which concepts need a simpler first pass. The product improves because corrections are reused, not because one chat happened once.

### Preference Loop - 5/5
**What you capture today:** MindBridge captures format choices such as Plain Steps, Story, Visual Map, Listen, and Practice, plus reading level, text size, audio use, session length, pace, examples that land, formats the learner avoids, and whether the learner prefers checklists or one-page study sheets.
**How it compounds:** Those choices become a persistent learner profile that changes the defaults. If a learner finishes work when MindBridge starts with short steps and practice, the next upload starts there. Preference becomes switching cost because a generic chatbot starts blank while MindBridge starts already tuned to the learner.

### Domain Context Loop - 2/5
**What you capture today:** MindBridge captures concepts, misconceptions, vocabulary, and course context inside a subject. Some transfer exists for study skills, explanation patterns, and common misconception shapes, but subject mastery stays mostly local to the course where it was learned.
**How it compounds:** This is the weakest loop because getting better at sociology does not automatically make MindBridge better at chemistry. The fix is to separate subject facts from reusable reasoning patterns, such as cause and effect chains, definitions, compare and contrast, timeline reasoning, and evidence use, then measure whether a pattern learned in one course improves first-pass quality in an adjacent course.

### Network Loop - 3/5
**What you capture today:** With consent and strong privacy controls, MindBridge can aggregate anonymized patterns: concepts many learners miss, explanations with high correction rates, practice questions that predict mastery, and formats that tend to work for similar learner profiles.
**How it compounds:** New learners benefit from prior learners' corrected paths, especially in common courses and common concepts. The loop is only moderate because neurodivergent learner data is sensitive, cohorts are fragmented by school and course, and raw student work cannot be shared casually.

**Total Flywheel Score: 15/20**
**Weakest Loop:** Domain Context Loop, 2/5.
**Fix for weakest loop:** Build a transfer layer that tags reusable reasoning patterns and misconception types separately from subject facts, then test whether those tags improve first-pass lesson quality in a new subject without lowering factual accuracy.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Microsoft Copilot and Google Gemini inside school productivity suites, with OpenAI and ChatGPT memory and file workflows as the consumer version of the same threat.
**Vector:** Bundle "explain this simply," read-aloud, study guides, flashcards, and quiz generation into tools students already open for class, then win before learners build a MindBridge profile.
**Time-to-threat:** Now to 6 months.
**% of value at risk:** 50% of the basic adaptation value. Generic generation is easy to copy. The learner profile, correction history, misconception map, and outcome evidence are harder to copy.

### 2. Vertical Competitor
**Attacker:** Canvas and other LMS platforms, or a study app that adds neurodivergent learning profiles.
**Vector:** Put adaptation inside the course shell where assignments, due dates, rubrics, and grades already live, then sell it to schools as accessibility and student success support.
**Time-to-threat:** 6 to 12 months.
**% of value at risk:** 35%. They own distribution and course context, but they may stay generic and compliance driven rather than tuned to the individual learner.

### 3. Adjacent Expansion
**Attacker:** Khan Academy, Quizlet, Grammarly, Notion, or a tutoring marketplace adding AI study adaptation.
**Vector:** Start from an existing student habit, add upload and personalized study paths, and use brand trust plus free tiers to compress price.
**Time-to-threat:** 3 to 9 months.
**% of value at risk:** 30%. They can win casual users. MindBridge defends by serving learners whose needs are not met by generic study help.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:** Microsoft and Google platform team.
**Attack vector (target the weakest loop):** Attack the Domain Context Loop by shipping cross-subject study help everywhere at once. If the suite can help in every class, MindBridge looks narrow even if it is deeper for one learner.
**Weeks 1-4 - what they ship:** A free Study Mode inside the school suite: select a class file, simplify it, listen to it, generate flashcards and practice, and save the result next to the assignment.
**Weeks 5-8 - how they poach users:** Make it the default in school accounts, remove the need for a new login, let teachers share it directly, and give administrators accessibility dashboards.
**Weeks 9-12 - why users don't come back:** Student files, classes, and study artifacts already live in the suite. "Good enough" in the tool they already use beats a separate product they have to remember to open.
**Your defense:** Do not compete on generic generation. Own the learner profile and evidence loop: persistent preferences, correction history, misconception map, teacher-aligned practice, and measured concept gains for neurodivergent learners. Integrate with the LMS and suites, make export easy, and prove outcomes the bundled feature does not measure.
