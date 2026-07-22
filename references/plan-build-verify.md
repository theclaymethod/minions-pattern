# Plan → build → verify

Preserve the Arbitrage discipline: use the host for routing, integration, and final judgment while workers perform as much bounded execution as practical. Choose either provider according to quota and task fit rather than enforcing a one-way Claude-to-Codex handoff.

1. The host captures user intent and decomposes the request into coherent units.
2. Delegate bounded discovery, plan drafts, architecture options, and risk analysis. The host resolves material ambiguity and freezes a short spec from that evidence: objective, constraints, non-goals, ownership boundaries, and exact acceptance checks.
3. Select one worker for each coherent implementation or check unit using quota first and task fit second.
4. Dispatch self-contained work orders with explicit stop points. Run units concurrently only when their write sets do not overlap; keep depth one unless the user requests recursive delegation.
5. Have workers execute implementation and acceptance checks, then inspect the actual diff, artifacts, and check output in the host.
6. When adversarial mode is on, follow `adversarial-review.md`. When it is off, skip the independent verifier but retain host validation of the evidence.
7. On `REQUEST_CHANGES`, return concrete findings to the original worker once. On a second miss, escalate the model; the host may take over only after that route is exhausted.
8. Independently validate evidence material to acceptance, integrate the result, and report the routing ledger. If the host executed any unit directly, include the applicable exception.
