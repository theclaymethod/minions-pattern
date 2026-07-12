# Claude calls Codex

Read this only when a Claude host delegates work or verification to GPT. The dispatched Codex process is an external CLI session, not a native Claude subagent, so it will not appear in Claude's agent tree.

## Select the GPT role

| Task | Model | Effort | Sandbox |
|---|---|---|---|
| Read-only scan | `gpt-5.6-luna` | `xhigh` | `read-only` |
| Routine implementation | `gpt-5.6-sol` | `medium` | `workspace-write` |
| Deep implementation | `gpt-5.6-sol` | `high` | `workspace-write` |
| Adversarial verification | `gpt-5.6-sol` | `high` | `read-only` |

Confirm model aliases locally before dispatch. If an alias is unavailable, use the nearest supported equivalent and record the substitution.

## Run the command

Write the shared dispatch contract to a prompt file. Use absolute, unique prompt and result paths for concurrent runs, then invoke:

```bash
codex exec -C "$REPO" \
  -m "$MODEL" \
  -c "model_reasoning_effort=\"$EFFORT\"" \
  -s "$SANDBOX" \
  -o "$RESULT" \
  - <"$PROMPT"
```

Use Claude Code's background-task support for independent runs. Do not hide stderr until the command has started successfully; stderr contains useful startup and failure diagnostics. Read the final result from `$RESULT`, then inspect the actual diff or artifacts in the Claude host.

## Guardrails

- Tell the Codex worker not to spawn subagents.
- Keep commits, pushes, releases, and destructive operations in the Claude host.
- Use read-only sandboxing for scans and adversarial review.
- Give one worker a coherent ownership boundary and exact acceptance commands.
- Use a fresh run for independent work; resume only when a correction needs the prior worker context.
- Never enable Ultra or fast mode from this runbook.
