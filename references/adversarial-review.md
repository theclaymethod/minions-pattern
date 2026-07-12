# Adversarial review

Use this reference only when adversarial mode is `on`.

## Choose the verifier

Use a stronger model from the provider that did not perform the work. Review is input-heavy and output-light, so prefer intelligence over generation economy.

- Claude worker → Sol High verifier.
- GPT worker → Opus High verifier.
- Architecture, security, data-loss risk, or large cross-cutting changes → consider Sol Max or Fable High/Max.
- Small, low-risk diffs under quota pressure → Sol Medium or Sonnet High is acceptable.

Give the verifier the objective, constraints, acceptance criteria, and actual diff or artifact. Withhold the worker's rationale unless it is necessary evidence so the framing remains independent.

Require one verdict:

```text
APPROVE         No material finding; acceptance evidence is sufficient.
REQUEST_CHANGES Concrete correctable finding with an artifact anchor.
BLOCK           Unsafe premise, missing evidence, or fundamental design failure.
```

Return evidence-backed findings to the original worker once. After a second miss, escalate or let the host take over. The host still inspects the result and runs the final checks.
