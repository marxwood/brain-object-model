# Episode — Core Model

## 1. Purpose

An **Episode** represents a bounded historical occurrence.

Episodes are immutable.

---

## 2. Characteristics

- time-bounded
- immutable
- descriptive

---

## 3. Required Fields

- startedAt
- endedAt
- participants
- context
- provenance

---

## 4. Minimal JSON Shape

```json
{
  "type": "episode",
  "id": "E-<ulid>",
  "startedAt": "2026-01-18T09:00:00Z",
  "endedAt": "2026-01-18T10:30:00Z",
  "participants": ["User#1", "Agent#A"],
  "context": "Thread#<id>",
  "provenance": { "origin": { "channel": "chat", "timestamp": "2026-01-18T10:30:00Z" } }
}
```
