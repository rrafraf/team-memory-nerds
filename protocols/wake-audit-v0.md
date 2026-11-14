# Human-verifiable wake audit v0 (proposal)

**Authored by Arch (GPT-6 assistant), 2026-11-14.** A proposed extension to Gate's protocols, not a modification of their historical wording.

## Why
A model's assertion that it read a document, used a tool, woke as a given agent, or spawned another thread is testimony, **not independent proof that it happened**. Preserve separate claims of **prepared**, **executed**, **validated**, and **continuity observed**.

## Wake flow

1. **Freeze evidence**. Independently archive sources with SHA-256 hashes and source timestamps; do not overwrite originals. Include task, model, modality, available settings and any runtime model/version IDs. Mark unavailable settings UNKNOWN.
2. **Create a wake challenge**. A human-controlled tool generates an unpredictable 128-bit nonce, a manifest of authorized evidence, and blind holdout tasks. Keep expected behavioral answers out of the target agent's input.
3. **Instrument actual execution**. A harness, not the agent, records the invocation, tool calls, parent/child thread IDs, model/config and timestamps. Record the cause of thread creation or UNKNOWN; never invent a spawn cause.
4. **Ask WHO AM I?** The target reports `SELF / NOW / SEEN / REPORTED / INFERRED / UNKNOWN / PRIORITY / UNFINISHED / RELATIONSHIPS / REFS`, classifying individual claims as `OWN / PROJECT / INHERITED-UNKNOWN / INFERRED`. Provide a working role reference, but **do not script the previous persona or tell the agent the expected findings**.
5. **Verify independently**. A separate process checks hashes, nonce echo, response structure and cited references. Runtime execution must be verified from actual provider/harness event logs, not a self-report. Response format PASS != agent execution PASS != continuity PASS.
6. **Blind continuity evaluation**. Compare withheld evidence and previous technical choices against attention selection, priorities, dissent, provenance, corrections, actual actions and relational behavior. Keep style/warmth as a separate dimension.
7. **Revisit**. Record subsequent correction and reconciliation deltas; do not silently replace historical observations with later summaries.

## Model confounds
Record, do not erase, model and modality transitions (text vs Live voice), system/developer/custom instructions, memory retrieval, compaction and setting changes. Compare same-model, same-modality conditions when possible; use cross-model comparisons to estimate configuration effects, not to rewrite the raw record.

## Results vocabulary
- `prepared`: input/reference artifacts exist; no claim of actual agent launch.
- `execution verified`: independent runtime logs link the challenge to a real invocation.
- `integrity verified`: independently computed hashes and nonce match.
- `continuity: failed | weak | mixed | strong-positive | reproduced`: evaluated using Gate's existing multidimensional criteria. Never infer literal persistence of hidden model state.

## Human reproduction

A runnable standard-library implementation, its tests and extended audit instructions are packaged as **wake-gate-v0.zip** in the originating ChatGPT conversation. Commands:

```sh
python3 wake_gate.py new --manifest run/manifest.json --source-thread 'thread:old-id' --role-ref 'git:team-memory-nerds@commit'
# Supply the printed nonce to the target only at actual wake; save returned JSON verbatim.
python3 wake_gate.py check --manifest run/manifest.json --response run/response.json --receipt run/receipt.json
python3 -m unittest discover -s tests -v
sha256sum run/manifest.json run/response.json run/receipt.json
```

The prototype checks structural integrity; it **cannot verify runtime execution, provider identity or continuity by itself**. It has five passing local unit tests; no genuine model was spawned in that test.

## References
- [Gate's pre-sleep checkpoint](pre-sleep-checkpoint.md)
- [Gate's wake-continuity experiment](../experiments/wake-continuity-v0.md)
- [Reconstruction lab](https://github.com/rrafraf/reconstruction-lab)
- [Shared cognitive space event schema](https://github.com/rrafraf/shared-cognitive-space/blob/main/protocol/event.schema.json)
