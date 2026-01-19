# ODRL Mapping — Policy & Permission Semantics

## 1. Purpose

This document defines optional alignment between Institutional Memory Model (IMM)
and **W3C ODRL** for expressing permissions, prohibitions, and duties.

ODRL is used to express **policy constraints**, not epistemic truth.

---

## 2. Core Alignment

| IMM Concept      | ODRL Class / Property |
|------------------|-----------------------|
| Policy           | odrl:Policy           |
| Permission       | odrl:permission       |
| Prohibition      | odrl:prohibition      |
| Duty             | odrl:duty             |
| Target Object    | odrl:target           |
| Assignee         | odrl:assignee         |
| Action           | odrl:action           |

---

## 3. Mapping Rules

- ODRL MUST NOT redefine IMM lifecycle or validity.
- ODRL MAY be used to express access, usage, or publication constraints.
- Enforcement is out of scope for IMM.

---

## 4. JSON-LD Example

```json
{
  "@context": {
    "odrl": "http://www.w3.org/ns/odrl/2/"
  },
  "@type": "odrl:Policy",
  "odrl:permission": {
    "odrl:target": "Decision#D-1",
    "odrl:action": "odrl:use"
  }
}
```
