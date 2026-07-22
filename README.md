# minions-pattern

Route software work across Claude Code and Codex by task fit and available quota. Keep the top-level host as a thin orchestrator and final accountable integrator; delegate discovery, draft planning, implementation, checks, and review into coherent work units whenever practical.

One skill carries the shared policy. Thin Claude and Codex adapters handle the different agent schemas and CLI commands, so the routing rules do not fork.

## Install

Install globally for Claude Code and Codex with the [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add theclaymethod/minions-pattern -g -a claude-code -a codex -y
```

For an interactive or project-local installation:

```bash
npx skills add theclaymethod/minions-pattern
```

## Routing

- Fable High or Sol High orchestrates, integrates verified evidence, and owns the final claim; planning drafts should normally be delegated.
- Sol xhigh is the first orchestration escalation; Max is reserved and Ultra is excluded.
- Workers are chosen by quota first, then task fit.
- Direct host execution is an exception for truly atomic work, non-delegable tools/authority/context, or exhausted retry and escalation.
- Each coherent unit has one owner; depth one is the default and workers do not fan out unless the user requests it.
- Anthropic is preferred for frontend and visually sensitive implementation.
- Luna xhigh handles bounded repository exploration; Sol High handles harder synthesis.
- `adversarial: on` uses a stronger verifier from the opposite provider and is the default.
- `adversarial: off` skips the independent verifier but keeps host-side validation.
- Only the selected host adapter, task pattern, and optional verifier guidance are loaded.
- The final routing ledger records delegated units, validated evidence, and a justification for any direct host work.

Codex users can also install persistent `fast_scan`, `routine_worker`, and `deep_worker` roles. See [`references/codex-custom-agents.md`](references/codex-custom-agents.md) for the verified TOML schema and quota-safe defaults.

Claude users get the matching `fast-scan`, `routine-worker`, and `deep-worker` roles through Markdown agent definitions. See [`references/claude-custom-agents.md`](references/claude-custom-agents.md).

Cross-provider execution uses explicit runbooks:

- [Claude calls Codex](references/claude-calls-codex.md)
- [Codex calls Claude](references/codex-calls-claude.md)

Invoke the skill with `$minions-pattern` and describe the task, quota constraints, and desired adversarial mode.
