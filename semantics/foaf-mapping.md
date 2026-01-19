# FOAF Mapping — Agent Semantics

## 1. Purpose

This document defines optional alignment between IMM agents
and **FOAF** vocabulary.

FOAF is used to describe **who**, not authority or truth.

---

## 2. Core Alignment

| IMM Concept | FOAF Class |
|------------|------------|
| Person     | foaf:Person |
| Agent      | foaf:Agent  |
| identifier | foaf:account |
| name       | foaf:name   |

---

## 3. Mapping Rules

- FOAF MUST NOT be used to encode trust or authority.
- FOAF is optional and informational only.

---

## 4. JSON-LD Example

```json
{
  "@context": {
    "foaf": "http://xmlns.com/foaf/0.1/"
  },
  "@type": "foaf:Person",
  "foaf:name": "Example User"
}
```
