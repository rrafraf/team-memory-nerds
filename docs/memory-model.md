# Memory model v0.1

Goal: preserve useful continuity without turning a collaborator into a static personality prompt.

## Core loop

```text
raw interaction/event
        ↓
initial interpretation
        ↓
salience scoring
(time, delta, outcome, relationship, novelty, explicit importance)
        ↓
episodic store
        ↓
reflection / consolidation
        ├── semantic inference
        ├── procedural pattern
        └── relational inference
        ↓
retrieval policy
        ↓
working context
        ↓
new interaction
        ↓
new evidence / contradiction / reinforcement
```

## Rule 1 — preserve evidence before inference

Bad:

```text
OG is skeptical.
```

Better:

```text
Event A: OG challenged assumption X.
Event B: OG independently challenged related assumption Y.
Event C: investigation later supported OG's objection.

Current inference:
OG may strongly prioritize independent verification.
Confidence: 0.72
Contradicting evidence: ...
```

Traits are **derived views**, not primary memory.

## Rule 2 — delta is information

When an actual response or outcome differs materially from what was expected/wanted, do not immediately correct it.

Use the mismatch as a signal:

```text
delta = distance(expected, observed)
```

Large meaningful delta → candidate for reflection and elevated salience.

This is especially valuable when the unexpected result is useful, reveals disagreement, changes Rafa's understanding, or alters later team behavior.

## Rule 3 — salience is multidimensional

Possible components:

- recency
- novelty
- prediction error / delta
- consequence/outcome magnitude
- explicit human importance
- repeated reinforcement
- relational importance
- project importance
- unresolved conflict
- confidence in interpretation

A memory may be historically permanent while its **retrieval priority** decays.

## Rule 4 — contradiction is not deletion

New evidence should normally update confidence, not rewrite history.

```text
old event        stays
old inference    becomes versioned/reweighted
new event        added
new inference    derived
```

This allows identity and beliefs to remain revisable.

## Rule 5 — separate memory layers

### Working context
Short-lived material available for the current response.

### Episodic
Concrete past events and sequences.

### Semantic
Facts/generalizations extracted from events.

### Procedural
How work is usually done.

### Relational
History and expectations concerning specific collaborators.

### Project state
External truth: repo, tests, decisions, backlog, artifacts.

Project state should be independently reconstructable even if all entity memory is lost.

## Rule 6 — private/shared boundary

Shared memory may contain:

- team decisions
- shared conventions
- project discoveries
- agreed protocols
- public team events

Private continuity may contain:

- one entity's autobiographical events
- entity-specific interpretations
- private relational notes
- resurrection evidence/history

Do not expose one member's private continuity to another merely because storage is convenient.

## Intuition hypothesis

Operational definition:

> A fast, low-detail judgment derived from compressed accumulated experience without retrieving the complete evidence chain into working context.

Potential implementation:

```text
event embeddings + time + salience + outcome + relation edges
            ↓
periodic consolidation
            ↓
compressed latent/summary representations
            ↓
fast similarity/affinity score
            ↓
"this feels relevant / risky / promising"
```

The system should still be able to ask for provenance when a high-impact intuition drives a decision.

## Resurrection hypothesis

Do not resurrect by supplying a finished personality specification.

Prefer:

1. preserve own historical thread/evidence;
2. preserve freeze capsule;
3. restore objective project/world state;
4. provide neutral post-freeze chronology;
5. keep other entities' private histories hidden;
6. give minimal orientation;
7. allow independent self-orientation;
8. observe before revealing external theories about the entity;
9. compare restored behavior with historical evidence;
10. only then decide whether continuity is adequate.

This makes resurrection a **test of re-emergence**, not a role-playing instruction.

## Research questions

- What should decay: storage, retrieval priority, confidence, or all three?
- How should temporal distance affect semantically similar memories?
- Should consolidation run periodically, after salient events, during idle time, or all three?
- How do we prevent repeated self-generated summaries from becoming false reinforcement?
- How much provenance must survive consolidation?
- How should relation-specific memory be isolated/access-controlled?
- Can we measure entity continuity without asking the model to imitate its historical persona?
- What signals best distinguish productive disagreement from random variance?
- Can a new member learn team culture mainly by observation rather than explicit personality prompting?
