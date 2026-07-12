# Routing examples

Use these as precedents, not fixed rules. Balance current quota before applying the provider preference.

## Complex feature planning

- Task: Design and plan a cross-cutting feature whose API and boundaries remain ambiguous.
- Pattern: `plan-build-verify`
- Planner: Fable High in Claude or Sol High in Codex; escalate to Max only if High is insufficient.
- Worker: none until the spec is frozen; then choose per implementation unit.
- Adversarial: on.
- Rationale: keep ambiguity and architecture in the strongest host before spending worker quota.

## Frozen backend implementation

- Task: Implement a clear backend plan with exact tests.
- Pattern: `plan-build-verify`
- Worker: Sol Medium or Sonnet Medium/High, chosen primarily by quota.
- Adversarial: on; use the stronger opposite provider.
- Rationale: routine code volume does not require the planner tier.

## Frontend feature

- Task: Build a responsive user-facing flow with visual and interaction requirements.
- Pattern: `frontend`
- Worker: prefer Sonnet or Opus when quota permits.
- Adversarial: on; use Sol High and include rendered evidence.
- Rationale: Anthropic is the default task-fit preference for frontend, while GPT supplies an independent check.

## Quick repository map

- Task: Locate the implementation of a behavior and summarize its control flow without editing.
- Pattern: `explore`
- Worker: Luna xhigh; escalate to Sol High when synthesis is inadequate or the decision is high risk.
- Adversarial: off unless the result drives a consequential architecture or security decision.
- Rationale: isolate context-heavy reading from the planner.

## Tiny organization action

- Task: Move files, organize folders, or perform a small clerical computer action.
- Pattern: none; direct dispatch only if the host should not do it.
- Worker: Haiku in Claude or Luna low/medium in Codex.
- Adversarial: off.
- Rationale: review and orchestration overhead exceed the task.

## Example entry template

```markdown
## <short task class>
- Task: <concrete request>
- Pattern: <pattern name or none>
- Worker: <model/effort and provider preference>
- Adversarial: <on or off; verifier if on>
- Rationale: <why this route is reusable>
```
