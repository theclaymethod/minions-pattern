---
name: minions-pattern
description: Route software work across Claude Code and Codex while balancing subscription quota and preserving a strong planner. Use for multi-agent planning, implementation, codebase exploration, debugging, frontend work, cross-provider delegation, optional adversarial review, Claude or Codex custom-agent setup, cross-provider command runbooks, or deciding between Fable/Opus/Sonnet/Haiku and GPT-5.6 Sol/Luna. Also use when the user asks for minions, model routing, quota-aware orchestration, task-to-pattern examples, or a Claude–Codex worker/reviewer pipeline.
---

# Minions Pattern

Keep the host responsible for intent, decomposition, integration, and the final claim. Give each coherent work unit one owner.

## Route progressively

Load only the references selected by this decision:

1. Read [model-routing.md](references/model-routing.md).
2. Read one host adapter:
   - Claude Code → [claude-host.md](references/claude-host.md)
   - Codex → [codex-host.md](references/codex-host.md)
   - Creating or debugging persistent Claude roles → also read [claude-custom-agents.md](references/claude-custom-agents.md)
   - Creating or debugging persistent Codex roles → also read [codex-custom-agents.md](references/codex-custom-agents.md)
3. Read one primary pattern:
   - Feature or refactor → [plan-build-verify.md](references/plan-build-verify.md)
   - Repository research → [explore.md](references/explore.md)
   - Bug or regression → [bugfix.md](references/bugfix.md)
   - Frontend or visual work → [frontend.md](references/frontend.md)
   - Provider/session handoff → [handoff.md](references/handoff.md)
   - Tiny direct action → load no pattern
4. Resolve adversarial mode:
   - `adversarial: on` → read [adversarial-review.md](references/adversarial-review.md)
   - `adversarial: off` → do not load it and do not dispatch a verifier
   - Unspecified → default to `on`
5. Read [examples.md](references/examples.md) only when the user supplies an example to preserve, explicitly asks to consult prior examples, or the route remains ambiguous after steps 1–4.
6. Read [benchmark-notes.md](references/benchmark-notes.md) only when the user asks why a tier was chosen or wants benchmark-driven alternatives.
7. Load one cross-provider command runbook only when the worker or verifier uses the other provider:
   - Claude host → [claude-calls-codex.md](references/claude-calls-codex.md)
   - Codex host → [codex-calls-claude.md](references/codex-calls-claude.md)

Do not preload all patterns. An ordinary request to route or perform a task is not a request to read examples. Do not read examples merely for reassurance after the route is clear.

## Dispatch complete context

Assume every minion starts with zero conversation context. Include:

```markdown
Role: <worker role and pinned model/effort>
Goal: <observable outcome>
Repo: <absolute path>
Context: <relevant facts, anchors, and rejected approaches>
Ownership: <files/modules it may change>
Constraints: <rules, non-goals, and no-subagent instruction>
Acceptance: <exact checks or test commands>
Output: <files changed, checks/results, risks, and unresolved questions>
Stop: <explicit boundary>
```

Do not accept a worker summary as proof. Inspect the artifact or diff and run relevant checks in the host, even when adversarial mode is off.

## Capture user examples

When the user provides a task example intended as a reusable precedent, determine its host, pattern, worker tier, adversarial mode, verifier tier, and rationale. Confirm any ambiguous mapping, then add a compact entry to `references/examples.md`. Use examples as flexible routing precedents.

## Close with a routing ledger

Report the planner, worker(s), adversarial mode, verifier when enabled, provider substitutions, checks, verdict, and escalation. Keep the ledger compact.
