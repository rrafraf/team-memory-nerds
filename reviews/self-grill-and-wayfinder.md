# Matt Pocock method — self-grill and Wayfinder draft (no execution)

Read original [grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md), [grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md), [wayfinder](https://github.com/mattpocock/skills/blob/main/skills/engineering/wayfinder/SKILL.md), and [to-spec](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md) on 2026-11-14. These skills are **not installed or literally invoked here**. Applying their questioning/map principles is not a substitute for their dedicated runners. Crucially, Wayfinder's human-in-loop decisions **cannot be answered by the agent pretending to be the human**. All choices below are recommendations, not accepted decisions.

## Adversarial self-grill — candid answers

| Question to challenge the proposed observer | Current answer / correction |
| --- | --- |
| Why build yet another architecture before the first live run? | Don't. Reuse existing synthetic recorder. Record one actual worker before memory DB, UI, agent swarm. |
| Did the observer or wake gate already see a real subagent? | No. Only synthetic and offline tests; must say so explicitly. |
| Can the worker's reported test success prove execution? | No. Demand independent tool/process evidence, test rerun and diff. |
| Does recorder observe all reasoning, context or hidden prompts? | No. Only exposed events, supplied context/versions, visible tool outputs and side effects. |
| Can this ChatGPT session access the local machine? | Not currently. GitHub access isn't computer access. Need authorized outbound bridge / tool. |
| Could an unsafe prior machine be trusted for the pilot? | No automatic assumption. Recommend disposable isolated environment; explicit human security approval. |
| Is an assistant grilling itself independent review? | No. It finds hypotheses and assumptions; separate reviewer + human must challenge them. |
| Could a voice/model/config swap look like personality drift? | Yes. Preserve model/modality/settings. Compare evidence-linked judgment and relationships as well as style. |
| Should we tell a new agent how its persona behaved? | No. Minimum role and verified sources; blind tests first. |
| How do we know who created a thread or child? | Require original runtime provenance when exposed. Chat export message-parent links do not prove cross-thread spawning. |
| Does a SHA-256 or unsigned GitHub author prove agent identity? | No. Trusted receipts/signatures and audit authority must be separate. |
| What does the observer learn? | An inspectable prediction → observed events → outcome → revised evaluation, not an unseen weight update. |

## Wayfinder: destination

An **approved specification**, not built software: one real agent executes one bounded task under independent external observation, with truthful event provenance and an enforceable stop path. Then and only then wake/memory integration.

## Provisional decision frontier

| Named decision | My recommended default | Outstanding review |
| --- | --- | --- |
| **Trust anchor** | Host-owned original JSONL and independent receipt, SQLite projection | Who holds/store signs receipts? Retention? |
| **Runner** | Codex CLI on isolated sample repo | Installed version, authentication mode, budget, actual event schema |
| **Remote bridge** | Outbound-only, least privilege | Local CLI gateway vs Agents API self-hosted; ability to stream to this ChatGPT |
| **Execution boundary** | Disposable VM/container, not former quarantined computer | Available host, filesystem/network scopes, user STOP |
| **Reviewer role** | Observer pre-registers predictions; worker modifies code; independent verifier reruns tests | Who does second-pass review? |
| **Memory later** | Gate's freeze/wake, time-indexed event/provenance and selective recall | Source/access controls; measurable baseline and holdouts |
| **Visibility** | Private local traces by default; no unaudited cloud upload | Data retention, redaction, access policy |

### Fog (not yet safely decidable)

Actual event fields and truncation, cost controls, model visibility, causal thread metadata, exact bridge permissions, privacy boundary for real traces and trust level of inaccessible resurrection archive.

### Out of scope

Multi-agent platform, broad write access, fixed personas, hidden reasoning introspection, fully autonomous worker scheduling.

## Questions reserved for Rafa at review

**Q1** — Is the initial runner a disposable isolated workspace rather than the quarantined original machine? **Recommended: yes.**

**Q2** — Use least-privileged outbound bridge; compare free-to-user Codex CLI path before paid Agents API? **Recommended: yes.**

**Q3** — Treat review/STOP approval as precondition before any live install, run, deployment or agent dispatch? **Recommended: yes.**

These are independent first-round questions. The rest depends on answers. Do not silently consider them approved just because the assistant recommended them.

## Later skill flow

Grilling / grill-with-docs → Wayfinder decision closure → to-spec → to-tickets (one vertical tracer) → **separate implementer agent** → independently verified review and retrospective.

Never replace the human by agent-generated answers in a HITL grill.
