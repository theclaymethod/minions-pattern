# Cross-provider handoff

Before dispatching or pausing unfinished work, verify repository reality with `git status` and the current branch. Pass what the next model cannot reconstruct, not a transcript.

Preserve the Baton discipline: record verified reality, intent, dead ends, and the literal next action. Do not use a handoff for completed work or as a substitute for durable architecture documentation.

```markdown
# Baton: <task>
TL;DR: <state and single next action>

## Intent and acceptance
<desired end state and exact checks>

## Verified state
<branch, committed work, uncommitted work, checks already run>

## Ownership and boundaries
<allowed files/areas and do-not-touch zones>

## Learnings and dead ends
<non-obvious discoveries and rejected approaches with reasons>

## Anchors
<paths, symbols, commands, artifacts>

## Next action
<literal first move and explicit stop point>

## Open questions
<decision plus current lean>
```

Require the receiving model to re-check the verified state before acting. Retire stale handoffs after integration.
