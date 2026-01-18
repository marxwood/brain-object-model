# Task — Core Model

## 1. Purpose

A **Task** represents an actionable intent.

---

## 2. Characteristics

- actionable
- bounded

---

## 3. Required Fields

- assignedTo
- createdAt
- objective
- status

---

## 4. Minimal JSON Shape

```json
{
  "type": "task",
  "id": "TK-<ulid>",
  "assignedTo": "Agent#A",
  "createdAt": "2026-01-18T08:30:00Z",
  "objective": "Verify claim CL-1",
  "status": "open"
}
```
