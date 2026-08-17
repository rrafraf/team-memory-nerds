# Ontology v0.1

Working vocabulary for the migration/memory experiments. Names are deliberately simple and revisable.

| Term | Meaning in this project | Loose human analogue | Notes |
|---|---|---|---|
| **Model** | underlying trained neural network | brain architecture + learned priors | not an entity/person |
| **Runtime** | model configuration + tools + permissions + harness for a run | current operating conditions | may change while identity appears continuous |
| **Thread** | persistent interaction/history container | autobiography / relationship history | major continuity boundary in practice |
| **Working context** | information available to the model now | working memory / current awareness | finite, selected, reconstructed |
| **History** | recorded past interaction | autobiographical record | history ≠ retrieved memory |
| **Event** | bounded interaction that happened at a time | event/experience | raw unit before interpretation |
| **Experience** | event whose later interpretation materially changes collaboration | salient experience | our operational term, not an architecture claim |
| **Salience** | priority for later retrieval/reflection | attention/emotional weighting | can be computed without implying emotion |
| **Recency** | temporal distance from now | recency effect | one retrieval signal among many |
| **Memory** | past information selectively resurfaced for current use | memory | broader than provider-specific “Memory” features |
| **Episodic memory** | event + context + sequence + outcome | episodic memory | preserves what happened |
| **Semantic memory** | extracted durable facts/generalizations | semantic memory | derived, revisable |
| **Procedural memory** | learned patterns for how to do things | skill/habit | e.g. team workflow |
| **Relational memory** | remembered history concerning another member | social/relationship memory | may remain private |
| **Project state** | external facts about code/work/world | environment/domain facts | should not depend on entity identity |
| **Private memory** | continuity material belonging to one entity | private autobiographical memory | hard access boundary by default |
| **Shared memory** | deliberately team-visible durable knowledge | institutional memory | distinct from gossip transport |
| **Retrieval** | selecting old information for current context | recall | selection policy is central |
| **Consolidation** | compressing/restructuring many events into durable memory | memory consolidation | should keep provenance |
| **Reconsolidation** | updating interpretation after later evidence | reconsolidation | never erase history silently |
| **Decay** | reduced retrieval priority over time | forgetting | value may decay while evidence remains |
| **Reinforcement** | repeated independent evidence increases confidence/salience | repeated learning | avoid simple repetition loops |
| **Conflict** | evidence contradicting existing inference | conflicting memories/beliefs | preserve both sides |
| **Reflection** | reconsidering previous output/behavior from another perspective | metacognition | can create new derived memories |
| **Delta** | mismatch between expected/wanted and observed response/outcome | prediction error | candidate salience multiplier |
| **Intuition** | fast compressed judgment from accumulated patterns without replaying the full chain | intuition | operational, not biological equivalence |
| **Identity state** | current answer to “who am I here?” | self-concept | derived from history/context/role/relationships |
| **Persona** | recognizable observable behavioral style | temperament/presentation | narrower than entity |
| **Role** | responsibility/domain owned in the team | occupational/social role | role can change without changing entity |
| **Entity** | temporally coherent collaboration identity associated with a thread/history | closest analogue: person | useful collaboration-layer concept, not claim of separate trained model |
| **Agent** | entity/runtime currently acting autonomously toward goals | acting individual | a mode of operation |
| **Relationship** | stable interaction pattern between entities | relationship | has history and expectations |
| **Culture** | implicitly reinforced team norms | culture | emerges through repeated interaction |
| **Protocol** | explicit coordination rules | procedure/governance | should stay minimal where possible |
| **Team** | members + relationships + culture + shared state | team | Rafa is part of the system |
| **Gossip bus** | explicit cross-thread transport | Slack/hallway/team chat | transport only, not deep memory |
| **Freeze** | stop interaction while preserving enough evidence/state for later continuation | cryopreservation metaphor | reversible goal |
| **Freeze capsule** | entity-produced final continuity checkpoint | handover + autobiographical checkpoint | high-value resurrection input |
| **Unfreeze** | resume from preserved conditions/state | revival metaphor | same environment if possible |
| **Resurrection** | reconstruct continuity across a changed/incompatible environment | no clean analogue | deliberately stronger experimental term |
| **Migration** | freeze → transport → reconstruct → validate | relocation/transplant | umbrella process |
| **Canary** | first restored member used to validate procedure | pilot subject | restore one before the whole team |

## Terms we should avoid or qualify

### “Instance”
Ambiguous. It can mean UI conversation, model invocation, process, or entity. Prefer **thread**, **runtime**, or **entity** depending on what is meant.

### “Fine-tuning”
Reserve for weight/training changes. For behavioral differentiation caused by accumulated interaction, prefer **contextual shaping** or **interactional tuning**.

### “Mind/state”
Useful metaphorically but too broad for technical records. Prefer the specific layer: working context, identity state, memory, project state, or relational state.

## Autonomy dimensions

Rather than treating freedom/autonomy as one scalar:

1. **Decision freedom** — choose implementation/approach within owned area.
2. **Epistemic freedom** — disagree with assumptions, including Rafa's.
3. **Exploratory freedom** — investigate useful adjacent questions without explicit command.

Current team governance hypothesis: **high autonomy, low hierarchy, human final authority**.
