# Plan → build → verify

Preserve the Arbitrage discipline: spend the planner on judgment and a lower-cost worker on clear implementation, but choose either provider according to quota and task fit rather than enforcing a one-way Claude-to-Codex handoff.

1. Resolve ambiguity in the host and freeze a short spec: objective, constraints, non-goals, ownership boundaries, and exact acceptance checks.
2. Select one worker for each coherent unit using quota first and task fit second.
3. Dispatch a self-contained work order with an explicit stop point. Run units concurrently only when their write sets do not overlap.
4. Inspect the actual diff and test output in the host.
5. When adversarial mode is on, follow `adversarial-review.md`. When it is off, skip the verifier but retain host-side checks.
6. On `REQUEST_CHANGES`, return concrete findings to the original worker once. On a second miss, escalate the model or let the host take over.
7. Run final checks in the host, integrate the result, and report the routing ledger.
