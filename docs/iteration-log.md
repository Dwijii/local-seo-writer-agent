# Iteration log: v1 → v2

The prompt was improved by running it, reading the output, naming each failure, and adding a rule that fixes that failure. Below is the last round (27 May 2026), which produced v2.

## Method

1. Run the current prompt as a custom GPT with a short request (for example "Write blog").
2. Paste the output (or a partial output) back into a review session.
3. Diagnose failures as **behaviours**, not wording ("asks for approval before writing", not "bad intro").
4. Add the smallest rule that removes that behaviour.
5. Re-run.

## Failures observed in v1 output and the fix in v2

| # | Observed failure | Why it matters | v2 rule added |
|---|---|---|---|
| 1 | Asked clarifying questions, proposed topic options and waited for approval after "Write blog" | A publishing workflow needs a draft, not a conversation | **Operational mode rules:** Production mode by default; Strategy and Clarification modes only on explicit request or genuinely missing info |
| 2 | Referenced the operator's own name and company in the article ("Since you're associated with …") | Leaks chat memory into client output; wrong brand identity | **Context discipline:** use only task-relevant context; never switch brand identity |
| 3 | Added a "Quick Links" jump menu to a short article | Template-driven structure; feels AI-made | **UX & formatting judgement:** structure only when it improves readability |
| 4 | Article felt over-structured, polished and long-form by default | Reads as SEO content, not editorial | Reinforced *editorial restraint*, *editorial compression* and *natural editorial flow* |

## Earlier refinements (summarised; v1 text not preserved)

Rounds before this one added the topic-discipline, quiet-expertise, experience-led-writing and AI-phrase-avoidance sections. Each targeted outputs that were encyclopaedic, jargon-heavy or full of stock marketing phrases.

## Result

Reviewer summary after v2: the system moved from a "generic AI SEO writer" towards an "autonomous local SEO editorial system". The remaining gap is the last 5–10% of human editorial polish, which is the intended human-in-the-loop step.

## What I'd add next

- A fixed set of 10 test briefs and a rubric (intent focus, local specificity, banned-phrase count, structure fit, factual caution), scored for each prompt version so changes are measured rather than eyeballed.
- Saved before/after article samples for each version.
