# Benchmark notes

Use this reference to explain owner preferences, not as an authoritative benchmark report.

## Stable conclusions used by the router

- Avoid Ultra for quota-sensitive orchestration. Public docs confirm that it enables proactive delegation and that each subagent consumes its own tokens.
- Use Sol High for the default orchestrator. Escalate to xhigh for genuinely difficult routing or evidence integration before reaching for Max; delegate planning drafts to a worker.
- Use Sol Medium for a worker following a frozen plan.
- Use Sol High for difficult debugging, architecture, security, or high-risk work.
- Use Luna xhigh for bounded read-only exploration. This is the owner's correction after testing; it replaces the earlier Terra High preference.
- Keep `max_depth = 1` to prevent child agents from spawning descendants. Limit parallelism to independent work even when `max_threads = 6` allows more open threads.

## Evidence boundary

OpenAI's current public subagent guide recommends Terra for fast, efficient exploration and does not document Luna in its model-choice section. The Luna xhigh route is the owner's local benchmark-driven policy. Label it as a local preference.

Do not repeat exact savings, benchmark scores, speed multipliers, or claims that Ultra always launches a fixed number of hidden agents unless the original benchmark or product source has been verified. Describe the practical mechanism instead: unpinned child settings may inherit or be chosen automatically, custom agent files can pin them, deeper fan-out consumes more tokens, and depth one prevents recursive descendants.
