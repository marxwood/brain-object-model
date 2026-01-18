# Thread — Core Model

## 1. Purpose

A **Thread** defines a contextual boundary.

---

## 2. Characteristics

- long-lived
- contextual
- non-epistemic

---

## 3. Required Fields

- openedAt
- openedBy
- scope
- status

---

## 4. Minimal JSON Shape

```json
{
  "type": "thread",
  "id": "T-<ulid>",
  "openedAt": "2026-01-18T08:00:00Z",
  "openedBy": "User#1",
  "scope": "Investigation",
  "status": "active"
}
```
