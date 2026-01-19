# Schema.org Mapping — Semantics

## 1. Purpose

This document defines **semantic alignment** between Institutional Memory Model
and schema.org vocabulary for interoperability.

Schema.org is used as a **lingua franca**, not as a truth model.

---

## 2. Mapping Principles

- IMM objects map to schema.org *types*, not pages
- Mapping is lossy by design
- IMM remains authoritative

---

## 3. Core Mappings

| IMM Object | schema.org Type |
|-----------|----------------|
| Entity    | Thing          |
| Person   | Person         |
| Place    | Place          |
| Episode  | Event          |
| Fact     | ClaimReview    |
| Claim    | Claim          |
| Decision | Action         |
| Task     | Action         |
| Question | Question       |

---

## 4. Non-mapped Concepts

The following have **no direct schema.org equivalent**:
- Validity lease
- Lifecycle status
- Conflict object

These MUST NOT be forced into schema.org.

---

## 5. JSON-LD Example

```json
{
  "@context": "https://schema.org",
  "@type": "Action",
  "name": "Decision: Select latest state",
  "agent": { "@type": "SoftwareApplication", "name": "BrainAgent" }
}
```

---

## 6. Compliance

Schema.org mapping is optional but recommended.
IMM semantics must never be distorted to fit schema.org.
