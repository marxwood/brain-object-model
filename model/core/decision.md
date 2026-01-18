# Decision — Core Model

## 1. Purpose

A **Decision** represents an explicit commitment, selection, or resolution
made in response to uncertainty, conflict, or choice.

Decisions are not facts.
Decisions are not states.

A Decision records **agency**.

---

## 2. Characteristics

- resolves ambiguity or conflict
- selects among alternatives
- may be revised only by another Decision
- always explicit and traceable

Decisions are action-authoritative, even if later proven wrong.

---

## 3. Required Fields

- context
- decidedBy
- decisionType
- subjectRefs
- rationale
- decidedAt
- provenance

---

## 4. Minimal JSON Shape

```json
{
  "type": "decision",
  "id": "D-<ulid>",
  "context": "Thread#<id>",
  "decisionType": "select",
  "subjectRefs": ["StateAssertion#ST-1"],
  "decidedBy": { "kind": "agent", "id": "Agent#Coordinator" },
  "rationale": "Most recent sensor reading",
  "decidedAt": "2026-01-18T11:00:00Z",
  "provenance": { "origin": { "channel": "system", "timestamp": "2026-01-18T11:00:00Z" } }
}
```

---

## 5. Compliance

Implicit decisions are forbidden.
