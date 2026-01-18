# Versioning Policy

This document defines the versioning rules for the **Brain Object Model (BOM)** specification.

BOM is a **specification**, not an implementation.
Versioning reflects changes to **conceptual contracts**, not code.

---

## Version Format

BOM uses the following format:

```
v<MAJOR>.<MINOR>
```

Examples:
- `v0.1`
- `v0.2`
- `v1.0`

Patch-level versions are intentionally omitted.

---

## Version Semantics

### MAJOR version
Incremented when:
- core epistemological principles change
- object roles or meanings are redefined
- backward compatibility of understanding is broken

MAJOR changes are expected to be rare.

---

### MINOR version
Incremented when:
- new objects are added
- existing objects gain new optional fields
- documentation or examples are expanded
- governance rules are clarified without changing intent

MINOR changes MUST NOT invalidate existing interpretations.

---

## Stability Phases

- `v0.x` — Foundation phase  
  Concepts are stable, but refinement is allowed.

- `v1.0` — Canon-stable  
  Epistemological model is frozen.
  Only extensions are permitted.

---

## Backward Compatibility

Backward compatibility refers to:
- conceptual meaning
- interpretability by agents and humans

It does NOT refer to:
- storage schemas
- APIs
- serialization formats

---

## Change Control

All version changes MUST:
- be explicit
- be documented
- reference the rationale for change

Silent version drift is forbidden.

---

## Current Status

**Current version: v0.1 (Foundation Complete)**

This version represents a closed epistemological foundation
aligned with System Momentum Canon and ADR-0.
