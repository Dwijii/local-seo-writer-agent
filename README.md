# Local SEO Writer Agent: prompt engineering case study

A reusable system prompt that turns a general LLM into an autonomous local-SEO publishing agent for trade businesses. It's deployed as one custom GPT per client and was improved through a run → review → fix loop.

> **Portfolio note.** Built in May 2026 for a UK electrical contractor through a marketing agency. Client names, locations and URLs are replaced with placeholders; examples are fictional.

## What this shows

- **Behaviour design, not just wording.** Explicit operating modes (Production, Strategy, Clarification) stop the classic chatbot failure of asking questions instead of producing work.
- **Iterative evaluation.** Each rule in v2 traces back to a failure observed in real output ([`docs/iteration-log.md`](docs/iteration-log.md)).
- **Multi-client architecture.** One base prompt with per-client config and knowledge, isolated in separate GPTs ([`docs/deployment-pattern.md`](docs/deployment-pattern.md)).
- **Guardrails for trust.** No invented statistics or URLs, cautious phrasing, banned AI phrases, publication-only output.

## Contents

| Path | What it is |
|---|---|
| [`prompts/system-prompt-v2.md`](prompts/system-prompt-v2.md) | The full v2 system prompt with client placeholders |
| [`docs/iteration-log.md`](docs/iteration-log.md) | Failures observed in v1 output and the rule that fixed each one |
| [`docs/deployment-pattern.md`](docs/deployment-pattern.md) | How it's deployed as per-client custom GPTs; the proposed multi-agent split |
| [`templates/client-brief.md`](templates/client-brief.md) | Values that fill the prompt placeholders |
| [`templates/content-plan-template.csv`](templates/content-plan-template.csv) | Knowledge-file format (fictional rows) |

## How to use it

1. Fill `templates/client-brief.md` for the client.
2. Replace the `{{…}}` placeholders in the prompt.
3. Create a custom GPT (or an API system prompt). Paste the prompt; upload the content plan as knowledge; turn on web search.
4. Ask: "Write blog". The agent picks the highest-value planned topic and writes a publish-ready draft.
5. A human editor does the final 5–10% polish and fact-check before publishing.

## My role

I ran the agent, judged the output, identified the failures and decided the fixes. ChatGPT helped draft the rule text. Deployment across client GPTs and the content-plan knowledge files were my setup.

## Status

v2 prompt complete and tested in iteration. Rollout to every client GPT is pending (see `docs/deployment-pattern.md`). The original v1 prompt and article samples were not preserved.

## Licence

MIT
