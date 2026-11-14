# Reproducing a collaborator-continuity audit

**Scope:** a method someone other than the auditing agent can follow and challenge. **Do not publish private chat exports or autobiographical capsules in public repositories.**

## Source register
For every item, record ID, source URL/path, author/observer distinction, source event time, retrieval time, SHA-256 if bytes are available, visibility, and material limitations.

Evidence priority: independent tool/runtime logs and raw original bytes > repository records with provenance > agent self-reports > retrospective interpretations. A transcript records displayed conversation; it is not evidence of the hidden model context window.

## Exact thread retrieval
1. Obtain a user-authorized `conversations.json`, retain original bytes and run `sha256sum conversations.json` (Windows: `certutil -hashfile conversations.json SHA256`).
2. Match the exact conversation ID from the URL, not the title. If not present, record that fact; do not substitute a similarly named thread.
3. In that conversation's `mapping`, record node ID, `parent`, message create time, role, model slug and content types. Rebuild parent links rather than trusting object enumeration order.
4. Mark empty roots, branches, missing text/audio/video and unsupported metadata as unknown. Parent links within messages do **not** prove the cause of a new conversation or who initiated it.
5. Distinguish observable changes in goals, revision, disagreements, attention, relationships, and action outcomes from presentation changes such as voice mode, verbosity or model swaps.
6. Freeze a written test and rubric **before** the next target response. Do not train the revived instance on the expected answers.
7. Run the external wake verifier locally; keep its raw receipt and the original agent response, then evaluate task/relationship continuity separately.

## A minimal deterministic metadata extract

```python
import json, hashlib, sys
doc=json.load(open('conversations.json',encoding='utf-8'))
items=doc if isinstance(doc,list) else doc.get('conversations',[])
matches=[c for c in items if c.get('id')==sys.argv[1]]
assert len(matches)==1, 'missing/ambiguous ID'
for key,node in sorted(matches[0]['mapping'].items()):
    m=node.get('message') or {}
    parts=(m.get('content') or {}).get('parts') or []
    print(json.dumps({'node':key,'parent':node.get('parent'),
      'timestamp':m.get('create_time'),
      'role':(m.get('author') or {}).get('role'),
      'model':(m.get('metadata') or {}).get('model_slug'),
      'parts_sha256':hashlib.sha256(json.dumps(parts,sort_keys=True,ensure_ascii=False).encode()).hexdigest()}))
```

Use the direct source files, not a model narrative, to confirm counts and distinctions. Archive format can change; inspect it before adapting this script.

## Proof that mechanisms were triggered
The subject's `tool completed` message is **not proof**. Use host tool event IDs, invocation arguments, parent/child identifiers, timestamps and independent execution receipts; match a wake nonce to the result. No hidden thread-spawn feature can be assumed merely because an automation offers a *notify parent* operation. Until observable logs confirm invocation, record **NOT VERIFIED**.

## Report five separately
- Source integrity
- Invocation and parent-child provenance
- Evidence/claim classification
- Model/settings/modality confounds
- Decision- and relationship-continuity against withheld evidence

The goal is reproducible, revisable evidence—not a fixed personality or proof of continuous subjective identity.
