# One real worker, independently observed — implementation plan for review

**Status:** NOT APPROVED TO IMPLEMENT. Planning artifact only.

## Objective

Rafa can watch one agent complete a bounded coding task, stop it, and personally verify what actually ran, which tools executed, what the outputs and side effects were, which conclusions were grounded, and which observations remain UNKNOWN.

```text
Rafa — goal, permissions, approvals, STOP
  |-- Observer / evaluator (assistant; predicts, audits, updates evaluation)
  |-- Worker (separate Codex agent; does the actual implementation)
  +-- Independent non-LLM recorder (outside worker's write scope)
         |-- raw runtime events + timestamps
         |-- original JSONL + externally held SHA-256 receipt
         |-- SQLite queryable projection + verified filesystem diff/tests
         +-- explicit process STOP result
```

**Principle:** the worker's `I ran it` is a claim, not proof. A hash shows equality to a known byte snapshot; without separately trusted provenance it does not certify authenticity, author or original time. An independent process captures evidence; human may rerun checks. Keep model self-reports separate from verifier outcomes.

## Reuse, don't rebuild

- First pilot: existing `agent-well-v1` / `subagent-observer-v0` external recorder and `codex exec --json`, which emits structured event JSONL. Validate event fields against the *installed runtime*, not guessed schemas. [Official eval example](https://developers.openai.com/blog/eval-skills).
- Later: [Codex app-server](https://developers.openai.com/blog/codex-as-a-platform) or [Agents API](https://developers.openai.com/api/docs/guides/agents-api/overview) if persistent turns, subagents, approvals and native trace export justify the added complexity.
- Local access: not available directly to this ChatGPT session. Compare two outbound-only bridges: (A) local Codex CLI + user-controlled authenticated gateway / MCP, and (B) official [self-hosted executor](https://developers.openai.com/api/docs/guides/agents-api/environments/self-hosted) using `codex exec-server` outbound WebSocket; B requires API/environment credentials, billed usage and a controller, **not direct ChatGPT access**. Neither bridge is installed or verified today.
- Keep privacy local by default. Source docs and project Git state remain authoritative; raw traces may contain prompts or secrets. No private archive pushed to public GitHub.
- Defer graph DB, full Oracle UI and memory integration until actual runtime evidence demonstrates the need. SQLite initially; later event-time vs knowledge-time and role/memory versioning.

## Stages and gates

| Gate | Reviewed task | Required evidence |
| --- | --- | --- |
| R0 | Review and approve plan | Human-approved goals, environment, evidence/privacy, stop and spend boundaries |
| R1 | Prepare isolated disposable workspace and outbound bridge | Permission/connection test, documented scope, independently testable disconnect |
| R2 | Replay and tamper tests | Clearly synthetic fixtures, corrupted traces rejected |
| R3 | First genuine one-agent run on safe sample repo | Actual process/provider events, tool calls where emitted, raw JSONL, STOP result |
| R4 | Separate worker implements one vertical telemetry seam: event → normalized store → receipt → verifier | Real code diff, rerun tests, linked trace of worker's own implementation |
| R5 | Observer compares predictions vs reality | Evidence-backed review: surprises, unsupported claims, missed events, proposed improvements |
| R6 | Introduce Gate's blind freeze/wake test and time-indexed memory | Context manifest, WHO AM I response, external invocation receipt, evidence-based continuity evaluation |
| R7 | Multiple children, OTLP/Langfuse, richer UI if proven useful | Demonstrated improvement over one-worker baseline |

## Distinct checks (must not collapse into a single PASS)

1. **Launch:** runtime actually began a turn; match run/session ID; don't infer `spawn_agent` from prompt text.
2. **Events:** tool invocations and results where emitted, parent-child linkage if available, timestamps with source/observer separation, missing/truncated data labeled.
3. **Effects:** independent verifier checks test exit, changed files, Git diff, permissions, process status, not just assistant narrative.
4. **Integrity:** append-only-ish recorder outside worker writable area, hash output, receipt stored separately and verified by a human-run command.
5. **STOP:** process group cancel / timeout demonstrated, plus acknowledged limitations: locally stopping does not guarantee refund or server-side spend cap.
6. **Safety:** isolated disposable VM/container with no personal home mounts, no credentials and constrained outbound network; do not use previously quarantined machine as first target.
7. **Learning:** observer pre-registers expected events and potential failure; compares to trace, updates postmortem and procedure. Not a claim of adjusting model weights.
8. **Continuity:** identify accessible context, memory, instruction revisions, model and modality; don't pretend to access hidden system state or chain-of-thought. Judge decisions, corrections and relationships separately from surface style.

## Stop conditions

Unexpected access/write, unapproved subprocess/network, missing trusted event stream, unverifiable spawn, secrets in traces, user STOP, non-reproducible diff/test, exceeded human-approved scope or unsafe expense.

## Not in first scope

No fixed persona prompting; no proof of literal identity; no automatic thread injection; no privileged local computer control; no production rollout; no swarm; no all-seeing CoT recorder.

After **R0 approval**, use the separate implementing agent for one isolated vertical slice. The observing assistant may evaluate but must not silently become the implementer or independent certifier.
