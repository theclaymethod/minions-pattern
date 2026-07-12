# Diagnose → repair → falsify

1. Reproduce the failure and identify the smallest falsifiable cause. Keep diagnosis separate from repair while the cause remains uncertain.
2. Freeze a repair brief containing the reproduction, expected behavior, suspected area, regression-test requirement, and exact test command.
3. Give one worker ownership of both the repair and regression test.
4. When adversarial mode is on, ask a stronger model from the other provider to disprove the fix: inspect edge cases, run the reproduction, and detect behavior that was masked rather than corrected. When off, run that falsification pass in the host.
5. Return evidence-backed findings to the worker once. Escalate or take over after a second miss.

Do not widen a bug fix into an opportunistic refactor. Record adjacent issues separately.
