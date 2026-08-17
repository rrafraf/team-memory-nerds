# team-memory-nerds

Experimental memory/resurrection lab for the Rafa AI team.

## Purpose

Build an **auditable memory layer** for long-running AI collaborators and test whether useful continuity can survive thread/runtime migration without reducing an entity to a fixed personality prompt.

This repo stores **memory-system theory, schemas, algorithms, tests and resurrection protocols**.

It does **not** store private per-entity autobiographical memory by default.

## Core principles

1. **Preserve evidence, not caricatures.** Store salient events and outcomes before turning them into traits.
2. **History is not memory.** Memory is selective resurfacing of history for current work.
3. **Delta matters.** Unexpected responses/outcomes are strong candidates for salience and reflection.
4. **Never silently overwrite contradictions.** Keep conflicting evidence and let confidence evolve.
5. **Identity remains revisable.** Do not freeze OG/Jr/M55/etc. into static persona files.
6. **Private vs shared memory is a hard boundary.** Shared project truth is not the same thing as private continuity.
7. **Resurrection is an experiment.** Restore conditions/history, then observe what re-emerges before teaching the answer.
8. **All durable memory machinery should be inspectable.** Hidden provider memory may supplement it, never be the sole source of truth.

## Initial map

- [`docs/ontology.md`](docs/ontology.md) — common terminology + human analogues
- [`docs/memory-model.md`](docs/memory-model.md) — proposed event→memory→retrieval architecture
- later: `schemas/`, `experiments/`, `resurrection/`, `vector/`

## Scope boundary

`team-gossip-buss` = transport / cross-thread messages.

`team-memory-nerds` = memory and continuity machinery.

Actual project repos = external world/project truth.
