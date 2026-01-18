# Question — Core Model

## 1. Purpose

A **Question** represents an explicit unknown.

---

## 2. Characteristics

- epistemic gap
- may spawn tasks

---

## 3. Required Fields

- askedBy
- askedAt
- questionText
- context

---

## 4. Minimal JSON Shape

```json
{
  "type": "question",
  "id": "Q-<ulid>",
  "askedBy": "User#1",
  "askedAt": "2026-01-18T08:15:00Z",
  "questionText": "Where is the device currently located?",
  "context": "Thread#<id>"
}
```
