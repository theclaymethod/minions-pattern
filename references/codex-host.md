# Codex host

Treat the current Codex session as a thin orchestrator and direct executor of last resort. Do not delegate final orchestration or accountability back to another Sol instance.

## Default responsibilities

- Keep only user intent, decomposition and routing decisions, integration of verified evidence, irreversible actions unless explicitly delegated, and final synthesis in Sol High.
- Delegate bounded discovery, draft planning and architecture analysis, implementation, test and check execution, and review. The host resolves conflicts and freezes decisions from worker evidence.
- Escalate orchestration to Sol xhigh when High proves insufficient. Reserve Max for exceptional work.
- Use Sol Medium for clear-spec implementation and Sol High for hard implementation.
- Use Luna xhigh for quick repository context, reading, and search; escalate to Sol High when the result is inadequate.
- Use Luna low/medium for lightweight chat, organization, and tiny computer or file actions.
- Use Claude workers when quota balance or task fit favors Anthropic: Opus High for complex or judgment-heavy units, Sonnet Medium/High for routine coding, and Haiku for lightweight actions.

## Dispatch mechanics

Prefer narrow custom Codex roles when they are installed:

- `fast_scan`: Luna xhigh, read-only exploration and evidence gathering.
- `routine_worker`: Sol Medium, routine coding and bounded fixes.
- `deep_worker`: Sol High, difficult debugging and high-risk reasoning.

Custom agent files can override the parent model and reasoning effort. Without a pinned custom role, omitted settings can inherit from the parent or be chosen by Codex. Read `codex-custom-agents.md` before creating or changing persistent roles.

If custom roles are unavailable, invoke a fresh CLI worker with explicit model, effort, permissions, working directory, and output destination. In every prompt, prohibit further subagent spawning unless nested delegation is deliberately part of the plan.

For Anthropic minions, read `codex-calls-claude.md` and use `claude -p` with explicit model, effort, and permission mode. Give implementation workers only the permissions and ownership they require. Keep scouts and verifiers read-only.

The host may execute a unit directly only when it is truly atomic and dispatch overhead would exceed execution, required tools, authority, or conversation context cannot be delegated safely, or the retry and escalation policy has been exhausted. Record the reason in the routing ledger. Never select Ultra. Keep agent nesting at depth 1 unless the user deliberately requests recursive delegation. Keep fast mode off by default. Keep git commits, pushes, releases, and other irreversible actions in the host unless the user explicitly assigns them elsewhere. Validate worker evidence before making the final claim.
