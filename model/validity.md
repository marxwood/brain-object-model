# Validity (Lease Semantics) — Core Model

## 1. Purpose

Validity defines the **temporary right** of an object (most critically: a State Assertion or a Projection)
to be treated as **action-relevant** within a given context.

Validity is a **lease**, not ownership.

- Validity governs **what may influence action**.
- Validity is **context-bound**, **time-bound**, and **revocable**.
- Validity is the structural mechanism of **forgetting**.

This document specifies lease semantics required for BOM-compliant systems.

---

## 2. Scope

Validity applies to:

- StateAssertion (STM)
- Projection (if used in a SoT / EAS slice)
- optionally: CanonicalRecord (if implemented as a lease pointer)

Validity does **not** apply to:

- CanonNode (Canon is not lease-based)
- Fact / Claim as knowledge (existence is not leased)

---

## 3. Non-negotiable Rules

1. No action-critical object may exist without explicit validity semantics.
2. Validity is always **per Context**.
3. Validity must be **expirable**. Permanent validity is forbidden.
4. Expiration must be handled as a first-class state (expired / revoked), not silent disappearance.
5. If validity cannot be evaluated, the object must be treated as **invalid**.

---

## 4. Validity Modes

A validity lease MUST declare one mode.

### 4.1 until_time

Validity expires at a fixed timestamp.

Required fields:

- expiresAt (ISO-8601)

### 4.2 until_event

Validity expires when a specified event occurs.

Required fields:

- untilEvent (locator / id / event pattern)
- optionally: scope to restrict matching

### 4.3 until_changed

Validity expires when a change is observed for the same semantic slot.

Used for:

- last-known state slots (subject + predicate)
- cached snapshots

Required fields:

- slot definition (at minimum: subject + predicate)

---

## 5. Validity Status

Validity MUST be represented explicitly using one of:

- allowed — currently valid
- expired — lease ended by time or condition
- revoked — explicitly invalidated due to contradiction, error, or policy
- superseded — replaced by a newer object occupying the same slot

---

## 6. Required Fields (Normative)

A Validity record MUST include:

- subjectRef — the object whose validity is governed
- contextRef — context / thread identifier
- mode — one of: until_time | until_event | until_changed
- status — one of: allowed | expired | revoked | superseded
- validFrom — timestamp

Plus mode-specific fields:

- expiresAt for until_time
- untilEvent for until_event
- slot for until_changed

Optional but recommended:

- priority
- revocationReason
- revokedBy

If any required field is missing, the write MUST be rejected.

---

## 7. Deterministic Precedence

If multiple objects are allowed for the same slot in the same context, the system MUST:

- create or update a Conflict object, OR
- deterministically select one and revoke or supersede the rest, with trace

Precedence may use only:

- explicit validity status
- timestamps
- explicit priority
- explicit Decision trace

Silent heuristics are forbidden.

---

## 8. Forgetting as Structure

Forgetting is not deletion.

Forgetting is transitioning validity to:

- expired
- revoked
- superseded

Historical records should be retained for audit.

---

## 9. Minimal JSON Shape (Normative)

```json
{
  "type": "validity",
  "id": "V-<ulid>",
  "subjectRef": "StateAssertion#ST-<ulid>",
  "contextRef": "Thread#<id>",
  "mode": "until_changed",
  "status": "allowed",
  "validFrom": "2026-01-18T00:00:00Z",
  "expiresAt": null,
  "untilEvent": null,
  "slot": {
    "subject": "Entity#<id>",
    "predicate": "parkedAt"
  },
  "priority": 10,
  "revocationReason": null,
  "revokedBy": null
}
```

---

## 10. Write Admission Rules

1. Reject writes without contextRef.
2. Reject writes without mode.
3. Reject writes without status.
4. Reject allowed validity with no expiry semantics.
5. Reject until_time without expiresAt.
6. Reject until_event without untilEvent.
7. Reject until_changed without slot definition.
8. Require revocationReason and revokedBy where applicable.

---

## 11. Compliance Checklist

An implementation is compliant if:

- validity is explicit and expirable,
- conflicts are deterministic and traceable,
- expired or revoked objects do not drive action.

Violation leads to stale reality and epistemic drift.
