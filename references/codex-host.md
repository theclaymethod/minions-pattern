# Codex host

Treat the current Codex session as the orchestrator. Do not delegate the orchestration role back to another Sol instance.

## Default responsibilities

- Keep high-level planning, architecture, decomposition, integration, and final synthesis in Sol High.
- Escalate planning to Sol Max only when High proves insufficient or the task is exceptionally difficult.
- Use Sol Medium for clear-spec implementation and Sol High for hard implementation.
- Use Luna xhigh for quick repository context, reading, and search; escalate to Sol High when the result is inadequate.
- Use Luna low/medium for lightweight chat, organization, and tiny computer or file actions.
- Use Claude workers when quota balance or task fit favors Anthropic: Opus High for complex or judgment-heavy units, Sonnet Medium/High for routine coding, and Haiku for lightweight actions.

## Dispatch mechanics

Use native Codex subagents only when the harness can pin the requested model and effort. Otherwise invoke a fresh CLI worker explicitly so the parent model is not silently inherited. Pin the model, effort, workspace permissions, working directory, and output destination. In every prompt, prohibit further subagent spawning unless nested delegation is deliberately part of the plan.

For Anthropic minions, prefer Claude Code's native Agent/Workflow mechanism when available. From the shell, use `claude -p` with explicit `--model` and `--effort`; give implementation workers only the permissions and ownership they require. Keep scouts and verifiers read-only.

Illustrative Claude verifier shape:

```bash
claude -p \
  --model opus \
  --effort high \
  --permission-mode plan \
  <"$PROMPT" >"$RESULT"
```

Never select Ultra. Keep fast mode off by default. Keep git commits, pushes, releases, and other irreversible actions in the host unless the user explicitly assigns them elsewhere.
