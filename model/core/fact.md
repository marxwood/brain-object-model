# Fact & Claim — Core Model

## 1. Purpose

This document defines the distinction between **Claim** and **Fact** within the Institutional Memory Model (IMM).

The separation exists to prevent:

- opinion or assumption being treated as knowledge,
- premature stabilization of beliefs,
- silent promotion of transient state into truth.

A **Claim** is an asserted proposition.
A **Fact** is a verified, stabilized proposition.

---

## 2. Definitions

### 2.1 Claim

A Claim is a proposition asserted by an actor.

Characteristics:

- may be true or false,
- requires provenance,
- may have evidence refs,
- is subject to verification,
- is not action-authoritative by default.

Claims may originate from:

- human statements,
- agent inferences,
- imported documents,
- external systems.

A Claim exists in **knowledge space**, not in state space.

---

### 2.2 Fact

A Fact is a Claim that has passed a verification process
and is accepted as **stable knowledge** within a defined scope.

Characteristics:

- derived from one or more Claims,
- has explicit verification trace,
- is not leased (unlike State),
- may be revised only by explicit counter-verification.

Facts are **authoritative for reasoning**, but still auditable.

---

## 3. Non-negotiable Rules

1. A Claim MUST NOT be treated as a Fact without verification.
2. A Fact MUST reference the Claims it was derived from.
3. Verification MUST be explicit and traceable.
4. Facts MUST NOT depend on transient State Assertions.
5. Deletion of Facts is forbidden; revision requires trace.

---

## 4. Verification

Verification is an explicit process that may involve:

- corroborating evidence,
- trusted sources,
- repeated independent confirmations,
- formal review or decision,
- automated checks with human oversight.

The verification mechanism itself is **out of scope** for IMM,
but its result and trace are not.

---

## 5. Relationship to State

- State Assertions describe **what is currently assumed**.
- Claims describe **what is asserted**.
- Facts describe **what is accepted as true**.

A State Assertion MAY inform a Claim.
A Claim MAY be verified into a Fact.
A State Assertion MUST NOT directly become a Fact.

---

## 6. Required Fields

### 6.1 Claim (Normative)

A Claim MUST include:

- `subject` — entity reference
- `predicate` — proposition
- `object` — value or entity
- `provenance` — origin and refs
- `context` — scope / thread
- `assertedAt` — timestamp
- `confidence` — optional belief strength

### 6.2 Fact (Normative)

A Fact MUST include:

- `derivedFrom` — list of Claim references
- `verification` — verification record
- `provenance` — aggregated provenance
- `acceptedAt` — timestamp
- `scope` — where the Fact applies

---

## 7. Minimal JSON Shape (Normative)

### 7.1 Claim

```json
{
  "type": "claim",
  "id": "CL-<ulid>",
  "subject": "Entity#<id>",
  "predicate": "locatedIn",
  "object": "Place#<id>",
  "context": "Thread#<id>",
  "assertedAt": "2026-01-18T09:00:00Z",
  "confidence": 0.6,
  "provenance": {
    "origin": {
      "actor": { "kind": "human", "id": "User#<id>" },
      "channel": "chat",
      "timestamp": "2026-01-18T09:00:00Z"
    },
    "refs": []
  }
}
```

### 7.2 Fact

```json
{
  "type": "fact",
  "id": "FA-<ulid>",
  "derivedFrom": ["Claim#CL-<ulid>"],
  "verification": {
    "method": "corroboration",
    "verifiedBy": "Agent#Verifier",
    "verifiedAt": "2026-01-18T10:00:00Z"
  },
  "acceptedAt": "2026-01-18T10:01:00Z",
  "scope": "Global",
  "provenance": {
    "origin": {
      "actor": { "kind": "system", "id": "Verifier#1" },
      "channel": "verification",
      "timestamp": "2026-01-18T10:01:00Z"
    },
    "refs": []
  }
}
```

---

## 8. Write Admission Rules

A runtime MUST enforce:

1. Reject Claims without provenance.
2. Reject Facts without verification.
3. Reject Facts without derived Claims.
4. Prevent automatic Claim → Fact promotion.
5. Preserve revision history for Facts.

---

## 9. Compliance Checklist

An implementation is compliant if:

- Claims and Facts are distinct types,
- verification is explicit and auditable,
- Facts are stable and revisable only by trace,
- State is never promoted directly to Fact.

Violation leads to epistemic collapse.
