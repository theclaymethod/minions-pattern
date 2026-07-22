# Claude custom agents

Read this only when installing, reviewing, or troubleshooting persistent Claude Code roles. The current schema is documented in [Claude Code's subagent guide](https://code.claude.com/docs/en/sub-agents).

## What the schema supports

Place personal agents in `~/.claude/agents/` or project agents in `.claude/agents/`. Each Markdown file requires `name` and `description` in YAML frontmatter. Optional fields can pin `model`, `effort`, `tools`, `disallowedTools`, `permissionMode`, `maxTurns`, `skills`, `background`, and `isolation`.

Subagents start with fresh context and do not see the host conversation. They cannot spawn other subagents. Claude chooses them from the request, current context, and each agent's description; an `@agent-<name>` mention forces a particular role for one task.

## Recommended roles

Use the checked-in templates as the source for Claude-specific syntax:

- `assets/claude-agents/fast-scan.md`: Haiku High with read-only tools.
- `assets/claude-agents/routine-worker.md`: Sonnet Medium with bounded write tools.
- `assets/claude-agents/deep-worker.md`: Opus High for complex implementation and debugging.

Copy them into `~/.claude/agents/` for personal roles or `.claude/agents/` for project roles. The descriptions request proactive routing, while their tool lists omit the Agent tool.

## Permission boundary

The parent permission context can take precedence. In particular, a parent using `acceptEdits`, `auto`, or `bypassPermissions` may limit whether a child permission mode changes behavior. Treat tool allowlists as the primary capability boundary and keep the host responsible for git mutations and final evidence validation.

## Safe setup flow

1. Read existing agent files and Claude settings before proposing changes.
2. Preserve unrelated settings and confirm the installed model aliases.
3. Show all proposed agent files before copying.
4. Write only after the user approves the preview.
5. Restart Claude Code or open a new session after direct file edits so the roles load.

Keep the routing policy in this skill or an applicable `CLAUDE.md`. That policy should make the host a thin control plane, proactively delegate bounded discovery, draft planning, implementation, checks, and review, and require a justification for direct work. The agent files encode only the Claude-specific role implementation.
