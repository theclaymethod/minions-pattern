# minions-pattern

Route software work across Claude Code and Codex by task fit and available quota. Keep a strong model in the planner role, send coherent work units to the appropriate worker, and optionally verify the result with a stronger model from the other provider.

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

- Fable High or Sol High plans and integrates.
- Sol xhigh is the first planning escalation; Max is reserved and Ultra is excluded.
- Workers are chosen by quota first, then task fit.
- Anthropic is preferred for frontend and visually sensitive implementation.
- Luna xhigh handles bounded repository exploration; Sol High handles harder synthesis.
- `adversarial: on` uses a stronger verifier from the opposite provider and is the default.
- `adversarial: off` skips the independent verifier but keeps host-side validation.
- Only the selected host adapter, task pattern, and optional verifier guidance are loaded.

Codex users can also install persistent `fast_scan`, `routine_worker`, and `deep_worker` roles. See [`references/codex-custom-agents.md`](references/codex-custom-agents.md) for the verified TOML schema and quota-safe defaults.

Claude users get the matching `fast-scan`, `routine-worker`, and `deep-worker` roles through Markdown agent definitions. See [`references/claude-custom-agents.md`](references/claude-custom-agents.md).

Cross-provider execution uses explicit runbooks:

- [Claude calls Codex](references/claude-calls-codex.md)
- [Codex calls Claude](references/codex-calls-claude.md)

Invoke the skill with `$minions-pattern` and describe the task, quota constraints, and desired adversarial mode.
