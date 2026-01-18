# State Assertion (STM) — Core Model

## 1. Purpose

A **State Assertion** represents **short-term, context-bound, invalidatable** information about an entity.

It exists to prevent **state → fact leakage** and to enforce the system rule:

> State is not knowledge. State is a temporary operational hypothesis.

State Assertions are part of **STM (Short-Term Memory)** semantics.

---

## 2. Non-negotiable Rule

A State Assertion must never be treated as a Fact/Claim.

- Facts/Claims describe **stable knowledge** and require evidence and truth status.
- State Assertions describe **temporary world assumptions** and require validity semantics.

Any system that stores changing world states as Facts/Claims is **non-compliant**.

---

## 3. Required Fields

A State Assertion MUST include:

- **subject** — entity reference (required)
- **predicate** — relationship or attribute name (required)
- **object** — entity reference or value (required)
- **context** — context identifier / thread (required)
- **epistemicStatus** — one of:
  - `perception`
  - `inference`
  - `assumption`
  - `action`
- **validity** — a lease defining when the assertion expires (required)
- **provenance** — provenance bundle (required)
- **refs** — evidence references  
  (recommended; required for `perception` where available)

If any required field is missing, the write **MUST be rejected**.

---

## 4. Validity Semantics (Lease)

Validity is a **lease**, not ownership.  
A State Assertion is admissible only if it is explicitly time- or event-bounded.

A State Assertion MUST define one of the following validity modes.

### 4.1 `until_changed`

The assertion is valid until a change is detected for the same **subject + predicate**.

Typical use cases:

- last known location
- current operational status
- latest known configuration

Invalidation triggers:

- any new State Assertion for the same subject + predicate
- an explicit change event

---

### 4.2 `until_time`

The assertion expires at a specific timestamp.

Typical use cases:

- short-lived assumptions
- cached observations
- temporary operational states

---

### 4.3 `until_event`

The assertion expires when a specified event occurs.

Typical use cases:

- “valid until user confirms”
- “valid until publish completes”
- “valid until sensor update arrives”

---

### 4.4 Mandatory Expiry

If an implementation cannot determine expiry conditions, it **MUST** assume the assertion is **expired**.

Default “valid forever” is **forbidden**.

---

## 5. Conflict Handling

Two or more State Assertions may exist concurrently **only if**:

- they are explicitly scoped to different contexts, OR
- they are explicitly represented as competing hypotheses with separate validity leases

If multiple active assertions exist for the same **(context, subject, predicate)**:

- the system **MUST** create or update a `Conflict` object, OR
- the system **MUST** deterministically select one and revoke the rest  
  (recorded via a Decision or explicit selection trace)

Silent coexistence without conflict tracking is **forbidden**.

---

## 6. Relationship to Facts / Claims

### 6.1 Promotion Is Not Automatic

A State Assertion **MUST NOT** be promoted to a Fact/Claim automatically.

Promotion requires an explicit **Decision** and/or a verification workflow.

---

### 6.2 Derivation Is Allowed

Facts/Claims may be derived from **patterns over State Assertions**, such as:

- repeated confirmations over time
- stable invariants inferred from multiple Episodes
- transformation rules (not single-instance states)

The resulting Fact/Claim must be **independent of transient state**.

---

## 7. Minimal JSON Shape (Normative)

Implementations may choose any storage format, but the following structure is the **normative contract**:

```json
{
  "type": "state",
  "id": "ST-<ulid>",
  "subject": "Entity#<id>",
  "predicate": "parkedAt",
  "object": "Place#<id>",
  "context": "Thread#<id>",
  "epistemicStatus": "perception",
  "validity": {
    "mode": "until_changed",
    "expiresAt": null,
    "untilEvent": null
  },
  "provenance": {
    "author": { "kind": "human", "id": "User#<id>" },
    "origin": { "channel": "chatgpt", "sessionId": "<id>" },
    "confidence": 0.72,
    "method": "observed"
  },
  "refs": [
    {
      "kind": "message",
      "locator": "gmail:<messageId>",
      "quote": "short excerpt",
      "ts": "2026-01-05T10:41:36+01:00"
    }
  ],
  "createdAt": "2026-01-18T00:00:00Z",
  "updatedAt": "2026-01-18T00:00:00Z",
  "status": "active",
  "visibility": "private",
  "tags": ["stm", "state", "lease"]
}
```

Notes:

- `expiresAt` is required for `until_time`
- `untilEvent` is required for `until_event`
- For `until_changed`, explicit expiry is not required, but lease semantics still apply

---

## 8. Write Admission Rules (Normative)

A Brain / SoT runtime **MUST** enforce:

1. Reject writes missing `validity`
2. Reject writes with validity implying permanence
3. Reject writes missing `context`
4. Reject writes missing `epistemicStatus`
5. Reject writes attempting to store state as Fact/Claim
6. Superseded state assertions **MUST** be marked as revoked / expired with audit trace

---

## 9. Operational Guidance (Non-normative)

- Use State Assertions for:
  - locations
  - current statuses
  - last-known values
  - temporary estimates
- Use Facts/Claims for:
  - stable definitions
  - verified knowledge
  - invariant patterns
- Prefer:
  - `until_event` for workflows
  - `until_time` for caches
  - `until_changed` for last-known state

---

## 10. Compliance Checklist

An implementation is compliant if:

- every state write includes a lease
- expired states do not drive actions
- state never silently becomes fact
- conflicts are explicit or deterministically resolved

Violation of these rules will inevitably lead to **stale reality and systemic drift**.
