# PROV-O Mapping — Provenance Semantics

## 1. Purpose

This document defines alignment between Brain Object Model (BOM)
and **W3C PROV-O** for interoperable provenance semantics.

PROV-O is used to externalize **how knowledge was produced**,
not to redefine BOM epistemology.

---

## 2. Core Alignment

| BOM Concept        | PROV-O Class / Property |
|-------------------|-------------------------|
| Provenance        | prov:Entity             |
| Origin event      | prov:Activity           |
| Actor / Agent     | prov:Agent              |
| authoredBy        | prov:wasAssociatedWith  |
| derivedFrom       | prov:wasDerivedFrom     |
| createdAt         | prov:generatedAtTime    |

---

## 3. Mapping Rules

- Every BOM Provenance MAY be serialized as a prov:Entity.
- Origin activities MAY be serialized as prov:Activity.
- BOM remains authoritative; PROV-O is representational.

---

## 4. JSON-LD Example

```json
{
  "@context": {
    "prov": "http://www.w3.org/ns/prov#"
  },
  "@type": "prov:Entity",
  "prov:wasDerivedFrom": "Claim#CL-1",
  "prov:generatedAtTime": "2026-01-18T10:01:00Z"
}
```
