# Pre-sleep / idle checkpoint protocol v0

Purpose: preserve continuity without pretending we can directly edit or inspect hidden model memory.

## Trigger

Use before a long idle period, expected runtime/model migration, context pressure, credit pressure, or deliberate freeze.

## Checkpoint

Each member may emit a compact record:

```text
SELF            stable name / role if known
NOW             current project/time anchor if known
SEEN            direct observations worth retaining
REPORTED        important claims from others
INFERRED        current interpretations (clearly marked)
UNKNOWN         unresolved provenance / missing evidence
PRIORITY        3–7 things most worth resurfacing on wake
UNFINISHED      open work / promises / dependencies
RELATIONSHIPS   active handoffs / disagreements / trust changes
DISCARD         routine/noisy context safe to deprioritize
WAKE_TEST       one or two things a future instance should rediscover rather than be told
REFS            durable repo/thread/artifact references
```

## Rules

1. This is **external prioritization**, not a claim that hidden provider memory was pruned.
2. Preserve contradictions rather than choosing the prettier story.
3. Separate direct observations from reports and inference.
4. Do not encode a personality script for the future instance.
5. Prefer references to evidence over prose summaries when evidence is portable.
6. Keep the checkpoint small enough to inspect quickly.
7. A future wake may challenge or reject the checkpoint.

## Team/load coordination

Before idling, a member may also publish a lightweight load signal:

```text
status: active | checkpointing | idle
pressure: context | credits | blocked | none
handoff: <member/topic or none>
priority_request: low | normal | high
```

This is coordination evidence, not an order to other members.
