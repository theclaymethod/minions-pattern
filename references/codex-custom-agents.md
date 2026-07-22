# Codex custom agents

Read this only when installing, reviewing, or troubleshooting persistent Codex agent roles. The current public schema is documented in [OpenAI's subagents guide](https://developers.openai.com/codex/subagents).

## What the schema supports

Place personal agents in `~/.codex/agents/` or project agents in `.codex/agents/`. Each TOML file requires `name`, `description`, and `developer_instructions`. It may override normal session keys such as `model`, `model_reasoning_effort`, and `sandbox_mode`. Omitted keys inherit from the parent session.

Keep global thread controls in `config.toml`:

```toml
[agents]
max_threads = 6
max_depth = 1
```

Six threads and depth one are already the documented defaults. Set them explicitly when predictable quota behavior matters. Do not invent a prose `routing_policy` key under `[agents]`; the public schema does not define one. Put routing policy in this skill, an applicable `AGENTS.md`, and the custom agents' descriptions.

For always-on routing outside explicit skill invocation, add this policy to the applicable global or project `AGENTS.md`:

```markdown
When delegating Codex work:

- Use `fast_scan` for read-only search, exploration, dependency tracing, and evidence gathering.
- Use `routine_worker` for clear, bounded coding, tests, documentation, migrations, and routine fixes.
- Use `deep_worker` for difficult debugging, architecture, security-sensitive work, and ambiguous or high-risk tasks.
- Keep only intent, decomposition and routing, evidence integration, irreversible actions unless explicitly delegated, and the final claim in the host.
- Delegate bounded discovery, draft planning, implementation, check execution, and review whenever practical.
- Work directly only for a truly atomic unit whose dispatch overhead exceeds execution, a non-delegable tool/authority/context constraint, or exhausted retry and escalation; record the reason.
- Keep depth one and do not let workers spawn subagents unless the user requests recursive delegation.
```

## Recommended owner override

The official guide currently recommends Terra for efficient exploration. This skill intentionally uses Luna xhigh for `fast_scan` based on the owner's later benchmark correction. Confirm that the local Codex build exposes the `gpt-5.6-luna` alias before saving this profile; otherwise use the nearest available lightweight model and record the substitution.

Use the checked-in templates as the source for provider-specific syntax:

- `assets/codex-agents/fast-scan.toml`
- `assets/codex-agents/routine-worker.toml`
- `assets/codex-agents/deep-worker.toml`

Copy them into `~/.codex/agents/` for personal roles or `.codex/agents/` for project roles. Show their complete contents before copying when the user requests a preview-first setup.

## Safe setup flow

1. Read the existing config and agent files before proposing changes.
2. Confirm the local model aliases and preserve unrelated settings.
3. Show the complete proposed `config.toml` section, routing policy, and all agent files before saving.
4. Write only after the user approves the preview.
5. Start a new task after saving so the roles load cleanly.

Custom files solve model inheritance only when Codex actually selects that role. Ask for bounded delegation proactively, keep one owner per coherent unit, and avoid recursive fan-out. A simple but non-atomic task should still be delegated; only the documented exceptions belong directly in the host.
