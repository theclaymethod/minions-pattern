# Model routing

Treat aliases as roles rather than permanent product names. If an alias is unavailable, select the nearest current equivalent and record the substitution.

## Default ladder

| Level | Anthropic | GPT | Typical work |
|---|---|---|---|
| Planner | Fable High | Sol High | Ambiguity reduction, architecture, decomposition, final synthesis |
| Planner escalation | Fable Max | Sol xhigh | Genuinely difficult planning after High is insufficient |
| Strong worker/reviewer | Opus High | Sol High | Complex implementation, debugging, design judgment, adversarial review |
| Routine worker | Sonnet Medium/High | Sol Medium | Clear-spec coding, tests, migrations, refactors, tooling |
| Context scout | Sonnet or Haiku | Luna xhigh | Search, codebase mapping, dependency tracing, bounded research; escalate to Sol High when needed |
| Lightweight operator | Haiku | Luna low/medium | Chat, file organization, and tiny computer or clerical actions |

For Sol, move from High to xhigh before considering Max. Reserve Max for exceptional work and never select Ultra. Keep fast mode off unless the user explicitly values latency over quota.

## Routing invariants

- Balance Claude and Codex quota before preferring a provider; use task fit as the tie-breaker.
- Prefer Anthropic workers for frontend and visually sensitive implementation.
- Default planning to Fable High in Claude or Sol High in Codex.
- Escalate Sol planning from High to xhigh when task difficulty justifies it; reserve Max for exceptional cases.
- Skip delegation when dispatch costs more than doing a tiny, obvious task locally.
- Split at file, module, service, or API boundaries; never split one coherent unit between workers.
- Parallelize only independent units with non-overlapping ownership.
- Escalate after observed failure, not predicted difficulty.
- Stop after one corrective redispatch; on a second miss, escalate or let the host take over.

## Choose the worker

1. Check which provider has more usable quota.
2. If quota is roughly balanced, prefer the provider whose strengths match the unit:
   - Prefer Anthropic for frontend, visual polish, interaction judgment, and copy-sensitive work.
   - Prefer GPT for backend, tests, migrations, broad refactors, tooling, and mechanical implementation.
3. Choose the lowest tier that can reliably satisfy a frozen spec.
4. Raise effort or tier only after an observed miss or when the risk class itself requires stronger reasoning.

Do not route trivial work merely to balance quota. Dispatch overhead is still a cost.
