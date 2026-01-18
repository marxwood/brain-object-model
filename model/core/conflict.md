# Conflict — Core Model

## 1. Purpose

A **Conflict** records explicit contradiction.

---

## 2. Characteristics

- explicit
- auditable

---

## 3. Required Fields

- conflictingRefs
- detectedAt
- context

---

## 4. Minimal JSON Shape

```json
{
  "type": "conflict",
  "id": "C-<ulid>",
  "conflictingRefs": ["StateAssertion#ST-1", "StateAssertion#ST-2"],
  "detectedAt": "2026-01-18T10:45:00Z",
  "context": "Thread#<id>"
}
```
