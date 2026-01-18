# Provenance & Evidence — Core Model

## 1. Purpose

Provenance defines **where information comes from**, **how it was produced**, and **what evidence supports it**.

In the Brain Object Model (BOM), provenance is mandatory for:

- State Assertions
- Facts / Claims
- Decisions
- Episodes
- Conflicts

Without provenance, information is **non-actionable**.

---

## 2. Separation of Concerns

Provenance is composed of two orthogonal parts:

1. **Origin** — how the information entered the system.
2. **Evidence (Refs)** — what external or internal artifacts support it.

These must never be conflated.

---

## 3. Origin

Origin describes the **production channel and actor**, not the truth of the content.

### 3.1 Required Fields

An Origin record MUST include:

- `actor` — who produced or introduced the information  
  (human, agent, system, sensor)
- `channel` — interface or system of origin  
  (chat, email, api, import, sensor)
- `sessionId` — session or execution identifier (where applicable)
- `timestamp` — when the information was produced or ingested

Optional:

- `tool` — specific tool or model used
- `confidenceHint` — non-authoritative confidence at creation time

Origin MUST NOT:

- assert correctness
- imply verification
- replace evidence

---

## 4. Evidence (Refs)

Evidence represents **addressable artifacts** that can support, contest, or contextualize information.

Evidence is represented as a list of **Refs**.

### 4.1 Ref Structure

Each Ref MUST include:

- `kind` — message | document | image | audio | video | log | dataset | other
- `locator` — opaque pointer to the artifact
- `quote` — minimal stable excerpt or fingerprint
- `ts` — timestamp of the referenced artifact

Optional:

- `hash` — content hash (if available)
- `confidence` — confidence in relevance (not truth)

---

## 5. Locator Semantics

`locator` is an **opaque, implementation-defined pointer**.

It identifies _where_ the artifact lives, not _how_ to access it.

Examples:

- gmail:18c9e7b4f1e0a123
- slack:C12345678|1693439921.000200
- chatgpt:session/abc123#msg-17
- filesystem:/mnt/archive/documents/note-42.txt
- http:https://example.com/article#p3
- ipfs:QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco
- arango:collection/episodes/987654

The BOM does not define dereferencing logic.

---

## 6. Confidence

Confidence expresses **belief strength**, not truth.

Rules:

- Confidence is always numeric (0.0–1.0)
- Confidence is never mandatory
- Confidence MUST NOT be auto-increased
- Confidence decay over time is allowed

Confidence must never override validity or verification status.

---

## 7. Minimal JSON Shape (Normative)

```json
{
  "type": "provenance",
  "id": "P-<ulid>",
  "origin": {
    "actor": { "kind": "agent", "id": "Agent#A1" },
    "channel": "chat",
    "sessionId": "sess-123",
    "timestamp": "2026-01-18T10:12:00Z",
    "tool": "gpt-5.2",
    "confidenceHint": 0.6
  },
  "refs": [
    {
      "kind": "message",
      "locator": "gmail:18c9e7b4f1e0a123",
      "quote": "short excerpt",
      "ts": "2026-01-17T08:41:36Z",
      "hash": "sha256:..."
    }
  ]
}
```

---

## 8. Write Admission Rules

A runtime MUST enforce:

1. Reject objects without provenance.
2. Reject provenance without origin.
3. Reject refs without locator.
4. Reject refs without timestamp.
5. Treat missing evidence as reduced trust, not as falsehood.

---

## 9. Compliance Checklist

An implementation is compliant if:

- provenance is mandatory for all actionable objects,
- origin and evidence are distinct,
- locators are opaque and non-assumptive,
- confidence does not override validity.

Violation leads to unverifiable knowledge and narrative drift.
