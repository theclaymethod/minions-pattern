# Diagnose → repair → falsify

1. Delegate reproduction and diagnosis as a bounded unit: identify the smallest falsifiable cause and keep diagnosis separate from repair while the cause remains uncertain.
2. Freeze a repair brief containing the reproduction, expected behavior, suspected area, regression-test requirement, and exact test command.
3. Give one worker ownership of both the repair and regression test.
4. When adversarial mode is on, ask a stronger model from the other provider to disprove the fix: inspect edge cases, run the reproduction, and detect behavior that was masked rather than corrected. When off, omit the independent verifier; require repair-worker evidence and have the host validate it.
5. Return evidence-backed findings to the worker once. Escalate after a second miss; let the host take over only if escalation is exhausted.

Do not widen a bug fix into an opportunistic refactor. Record adjacent issues separately.
