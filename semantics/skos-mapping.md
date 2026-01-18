# SKOS Usage — Concept Semantics

## 1. Purpose

This document defines how **SKOS** may be used
to represent controlled vocabularies inside BOM.

SKOS is used for **labels**, not for reasoning.

---

## 2. Core Alignment

| BOM Concept | SKOS Property |
|------------|---------------|
| Concept    | skos:Concept  |
| label      | skos:prefLabel |
| alias      | skos:altLabel  |
| hierarchy  | skos:broader / narrower |

---

## 3. Mapping Rules

- SKOS MUST NOT be used to encode facts.
- SKOS MAY be used for tagging, categorization, UX.

---

## 4. JSON-LD Example

```json
{
  "@context": {
    "skos": "http://www.w3.org/2004/02/skos/core#"
  },
  "@type": "skos:Concept",
  "skos:prefLabel": "Decision"
}
```
