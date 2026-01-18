# Lifecycle — Core Model

## 1. Purpose

Lifecycle defines the **allowed state transitions** for Brain Object Model objects.
It prevents silent mutation, resurrection of expired objects, and uncontrolled drift.

Lifecycle is orthogonal to validity:
- lifecycle = what an object *is allowed to become*
- validity = whether an object *may influence action*

---

## 2. Universal Lifecycle States

All BOM objects MUST expose a lifecycle status:

- `created`
- `active`
- `superseded`
- `revoked`
- `archived`

Deletion is discouraged and non-normative.

---

## 3. State Transitions (Normative)

Allowed transitions:

- created → active
- active → superseded
- active → revoked
- superseded → archived
- revoked → archived

Forbidden transitions:

- archived → active
- revoked → active
- superseded → active

---

## 4. Revision Semantics

Objects MUST NOT be edited in-place once active.

Revision requires:
- creation of a new object
- explicit linkage (`supersedes`)
- audit trace

---

## 5. Compliance

Any system allowing silent in-place mutation is non-compliant.
