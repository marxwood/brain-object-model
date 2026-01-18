# Write Rules — Governance

## 1. Purpose

Write Rules define **hard rejection criteria** for Brain Object Model writes.
They are enforced at ingress.

---

## 2. Universal Rejections

A write MUST be rejected if:

- object type is unknown
- required fields are missing
- provenance is missing
- context is missing
- lifecycle status is invalid

---

## 3. Object-Specific Rejections

### StateAssertion
- missing validity lease
- permanent validity
- missing epistemicStatus

### Fact
- missing verification
- missing derived Claims

### Decision
- missing decidedBy
- missing rationale

---

## 4. Compliance

Write rules are mandatory.
Soft validation is forbidden.
