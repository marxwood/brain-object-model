# ADR-0 Compatibility Note

## 1. Purpose

This note defines how the **Brain Object Model (BOM)** is constrained by and compatible with the
**System Momentum Canon** and **ADR-0 (Epistemic Constraints)**.

BOM is a **derivative runtime specification**.
It does not create or modify canon. It implements canon constraints as enforceable structure.

---

## 2. Normative Relationship

- **Canon / ADR-0 are authoritative.**
- **BOM is subordinate.**
- In any conflict, **Canon and ADR-0 prevail**.

BOM must remain a reusable, replaceable derivative artifact.

---

## 3. ADR-0 Alignment Matrix

| ADR-0 Constraint (Principle) | BOM Mechanism |
|---|---|
| Provenance required for actionable knowledge | `model/provenance.md` mandatory `origin` + `refs` |
| Separate state from knowledge | `model/core/state.md` vs `model/core/fact.md` (Claim/Fact separation) |
| No implicit truth | `Decision` required for selection/authority; `Validity` leases gate action |
| Explicit contradiction handling | `model/core/conflict.md` (Conflict is first-class) |
| Auditability / traceability | immutable Episodes + provenance refs + revision via supersedes/revoked |
| No silent overwrites | lifecycle constraints + write rules reject in-place mutation |
| Forgetting is structural | `model/validity.md` lease expiry / revocation |
| Contextual validity (no global SoT) | `Thread` as scope + validity is always per contextRef |
| Human-in-the-loop where required | Decisions can be made by human actor; enforcement out of scope but trace supported |
| Prevent propaganda / dogma drift | mandatory plurality via conflict + deterministic resolution + expiry semantics (validity half-life) |

---

## 4. Non-Negotiable Invariants (Derived from ADR-0)

An implementation claiming BOM compliance MUST enforce:

1. **No write without provenance** for actionable objects.
2. **No state stored as fact** without verification trace.
3. **No action from expired / revoked validity**.
4. **No implicit decisions** (selection must be explicit and traceable).
5. **No silent overwrite of active objects** (revision must create a new object and link it).

---

## 5. Scope Guardrails

This note does not define ADR-0.
It only defines BOM’s conformance posture.

BOM MUST NOT:
- redefine canon terms,
- introduce moral or political truth rules,
- encode ideology,
- claim global truth authority.

---

## 6. Where This Note Lives

Recommended placement in this repository:

- `governance/adr0-compatibility.md`

Canon repo should contain only a **link/reference** to this note,
not a copied duplicate.

---

## 7. Implementation Implications (Non-Normative)

Typical compliance checks (examples):
- Reject `StateAssertion` with missing lease.
- Reject `Fact` without verification + derived claims.
- Reject any write missing provenance.
- Ensure conflict creation or deterministic resolution in same-context collisions.
- Ensure validity expiry is enforced before action execution.

---

## 8. Final Statement

BOM exists to operationalize ADR-0 discipline in a portable, cross-LLM data contract.

It is compliant by design only if implementations enforce its write rules and validity semantics.
