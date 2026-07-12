# Claude Code host

Treat the current Claude session as the orchestrator. Do not delegate the orchestration role back to another Fable instance.

## Default responsibilities

- Keep high-level planning, architecture, decomposition, integration, and final synthesis in Fable High.
- Use Opus High for complex implementation, debugging, judgment-heavy work, or review of GPT output.
- Use Sonnet Medium/High for clear-spec implementation, tests, migrations, and routine refactors.
- Use Haiku for lightweight chat, organization, and tiny computer or file actions.
- Use GPT workers when quota balance or task fit favors Codex: Sol Medium for routine implementation, Sol High for hard work, Luna xhigh for context gathering, and Luna low/medium for lightweight actions. Escalate weak scout synthesis to Sol High.

## Dispatch mechanics

Prefer Claude Code's native Agent/Workflow mechanism for Anthropic minions and pin the model and effort explicitly. For GPT minions, use `codex exec` with a prompt file or stdin; pin model, reasoning effort, working directory, sandbox, and output file. Do not rely on user defaults.

Use write access only for an implementation worker with explicit ownership. Use read-only access for scouts and verifiers. In every prompt, prohibit further subagent spawning unless nested delegation is deliberately part of the plan.

Illustrative GPT verifier shape:

```bash
codex exec -C "$REPO" \
  -m gpt-5.6-sol \
  -c model_reasoning_effort="high" \
  -s read-only \
  -o "$RESULT" - <"$PROMPT"
```

Do not enable fast mode or Ultra. Keep git commits, pushes, releases, and other irreversible actions in the host unless the user explicitly assigns them elsewhere.
