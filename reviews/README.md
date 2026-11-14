# Three Old Dogs — implementation review room (14 November 2026)

**DRAFT. Planning only. Do not implement, deploy, install or start autonomous agents until reviewed.**

**Destination:** one observable Codex worker completes a bounded implementation task in an isolated workspace while a separate observer independently captures real execution events, evaluates outcomes and records what was learned. Only after that is verified should continuity/wake memory be attached.

## Existing evidence and proposals — preserve original ownership

- [Gate's memory ontology and freeze/wake protocol](https://github.com/rrafraf/team-memory-nerds) — authoritative historical design; do not replace or quietly edit.
- [Wake audit draft PR](https://github.com/rrafraf/team-memory-nerds/pull/1) — human-verifiable nonce/hash/checkpoint gates, not proof of a live agent.
- [OG canary evidence draft PR](https://github.com/rrafraf/reconstruction-lab/pull/2) — historical positive result with explicit verification limits.
- [Reconstruction lab](https://github.com/rrafraf/reconstruction-lab) — historical evidence, blind tests, behavioral deltas.
- [Shared cognitive space](https://github.com/rrafraf/shared-cognitive-space) — observable events, provenance, visibility.
- [Hivemind observatory](https://github.com/rrafraf/hivemind-observatory) — Oracle's human-readable event projection.
- [Team gossip bus, OG wake issue](https://github.com/rrafraf/team-gossip-bus/issues/3) — communication and historical reports, not proof of arbitrary thread injection.

## Local prototype inventory, verified by SHA-256 from available bytes

| Archive | SHA-256 | Actual demonstrated state |
| --- | --- | --- |
| subagent-observer-v0.zip | `3e90382a875058ea2caf6916e86fe93f0a62416523e798919d8aebb940bab2f2` | Synthetic replay / recorder, **no real subagent** |
| agent-well-v1.zip | `7307ed716bfd644eb0e248306d51d9dd943c94dca699572430b4e82fcecad9c0` | SQLite event store and synthetic replay, **no real worker** |
| wake-gate-v0.zip | `c3aee8c6bff5350d3121c80575ee64f5df129da50b538df43956f4eed6c48f7b` | Offline nonce/hash/structure verifier, **five passing tests**, not execution/identity proof |

These ZIP files are conversation/Library artifacts, **not committed to this public repo**. They may contain source evidence unsuitable for public upload. Gate's original `20260817-133047.zip` and the derived Library `og-canary-wake-package.zip` are separate artifacts; contents/hashes of the latter have not been verified from this runtime.

## Review files

- [Observer-first plan](observer-first-plan.md): actual phases, trust boundaries, stop criteria and bridge choices.
- [Self-grill and Wayfinder](self-grill-and-wayfinder.md): adversarial questions and **provisional** decisions requiring human review.

No changes to Gate's historical files, no signing claim. The GitHub connector acts as Rafa's authenticated account; an assistant-authored commit message is not an independently signed agent identity.
