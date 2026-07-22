# Frontend implementation with visual judgment

Prefer an Anthropic worker when quota permits. Keep product intent and final visual acceptance in the host, while delegating design exploration and implementation judgment as bounded units.

1. Delegate a bounded design draft covering layout, states, interactions, responsiveness, accessibility, motion, and reference qualities; have the host freeze the acceptance intent.
2. Give one worker ownership of the coherent UI unit.
3. Run the interface, interact with it, and capture representative screenshots or recordings.
4. When adversarial mode is on, use the stronger other-provider verifier to compare the rendered result with the intent and probe behavior—not merely inspect code. When off, omit the independent verifier and have the host validate the worker's rendered evidence.
5. Redispatch concrete feedback: identify the element, observed mismatch, target behavior, and supporting evidence.
6. Stop after one correction round; escalate rather than burning repeated visual loops.

The host makes final subjective tradeoffs and performs visual acceptance.
