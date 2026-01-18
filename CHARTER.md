# Brain Object Model — Charter

## 1. Purpose

The Brain Object Model (BOM) defines the **admissible data structures and epistemic constraints**
for a **Brain / Source-of-Truth (SoT) runtime organ**.

Its purpose is to enable:

- cross-LLM continuity without implicit memory,
- interoperable agent interaction,
- auditable knowledge handling,
- strict separation between fact, state, decision, and interpretation.

BOM is a **technical specification**, not a philosophical or normative document.

---

## 2. Scope

This specification defines:

- object types and their boundaries,
- lifecycle and validity semantics,
- provenance and audit requirements,
- write-admission constraints,
- semantic mapping discipline (e.g. schema.org, PROV-O).

This specification does **not** define:

- truth, meaning, or values,
- moral, political, or strategic positions,
- inference logic or reasoning policies,
- implementation details (storage, APIs, deployment).

---

## 3. Authority & Constraints

This specification is a **derivative runtime model** constrained by:

- **System Momentum Canon**
- **ADR-0 (Epistemic Constraints)**

It must not violate Canon or ADR-0.
In case of conflict, **Canon and ADR-0 always prevail**.

BOM does not introduce new canonical truths.
It only specifies how truths, states, and decisions may be represented.

---

## 4. Non-Goals

The Brain Object Model explicitly rejects:

- implicit or emergent memory,
- untyped or free-form knowledge storage,
- state being treated as fact,
- silent overwriting of historical records,
- hidden inference or non-auditable mutation.

Any system exhibiting these behaviors is **non-compliant** with BOM.

---

## 5. Epistemic Discipline

All information handled through BOM must be explicitly classified as one of:

- **Fact / Claim** — asserted or verified knowledge with provenance,
- **State Assertion** — temporary, context-bound, invalidatable state,
- **Decision** — explicit resolution or commitment,
- **Episode** — historical occurrence or interaction,
- **Question / Task / Thread** — operational constructs.

No object may ambiguously cross these categories.

---

## 6. Versioning & Evolution

BOM follows semantic versioning principles.

- `v0.x` indicates an evolving specification with possible breaking changes.
- `v1.0` indicates a stable, production-ready data contract.

Backward compatibility is **not guaranteed** before `v1.0`.

---

## 7. Compliance

An implementation is considered **BOM-compliant** if and only if:

- it enforces object typing and boundaries,
- it preserves provenance and auditability,
- it prevents state-to-fact leakage,
- it respects Canon and ADR-0 constraints,
- it does not introduce implicit memory.

Compliance is structural, not behavioral.

---

## 8. Position in the System

The Brain Object Model is:

- a **runtime-facing specification**,
- a **reusable derivative artifact**,
- **not** a core system authority.

It may be adopted, extended, or replaced by other systems,
provided Canon and ADR-0 constraints remain intact.

---

## 9. Final Statement

The Brain Object Model does not define what is true.

It defines **how truth, state, and decisions are allowed to exist** in a system
that rejects illusionary memory and enforces epistemic discipline.
