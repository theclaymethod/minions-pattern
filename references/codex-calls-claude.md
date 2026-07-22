# Codex calls Claude

Read this only when a Codex host delegates work or verification to Claude. The dispatched Claude process is an external CLI session, not a native Codex subagent, so it will not appear in Codex's agent tree.

## Select the Claude role

| Task | Model | Effort | Permission mode |
|---|---|---|---|
| Read-only scan or tiny action | `haiku` | `high` | `plan` |
| Routine implementation | `sonnet` | `medium` | `acceptEdits` |
| Deep or frontend implementation | `opus` | `high` | `acceptEdits` |
| Adversarial verification | `opus` | `high` | `plan` |

Use task fit after quota balancing. Prefer Anthropic for frontend and visual judgment. Confirm aliases locally and record any substitution.

## Run the command

Write the shared dispatch contract to a prompt file and use absolute prompt and result paths. Claude Code has no working-directory flag equivalent to Codex `-C`, so start it from the repository:

```bash
(
  cd "$REPO" || exit 1
  claude -p \
    --model "$MODEL" \
    --effort "$EFFORT" \
    --permission-mode "$PERMISSION_MODE" \
    <"$PROMPT" >"$RESULT"
)
```

Add `--no-session-persistence` for one-shot scans and verification. Omit it when a worker may need a focused follow-up. Read `$RESULT`, then inspect the actual diff or artifacts in the Codex host.

## Guardrails

- Keep the prompt self-contained because the Claude process has none of the Codex conversation.
- Keep commits, pushes, releases, and destructive operations in the Codex host.
- Use `plan` for scans and adversarial verification.
- Give implementation workers explicit file ownership and acceptance commands.
- Run parallel workers only when their write sets do not overlap.
- Treat CLI success as transport success; the host still validates the work.
