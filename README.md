# Institutional Memory Model (IMM)

Institutional Memory Model (IMM) is a **specification-first epistemological model**
designed for AI agents and agentic systems.

Its purpose is to prevent epistemic collapse by strictly separating:
- assertions from verified knowledge,
- transient state from stable facts,
- reasoning from decision-making authority.

IMM is not a database schema, not an API, and not an ontology replacement.
It is a **conceptual contract** that other systems may implement.

---

## Core Principles

- **Claim ≠ Fact ≠ Decision**
- Nothing becomes a Fact without verification
- Nothing influences action without an explicit Decision
- Provenance is mandatory
- Conflicts must be explicit

---

## Repository Structure

```
institutional-memory-model/
├── CHARTER.md
├── README.md
├── scope.md
├── model/
├── governance/
├── semantics/
└── examples/
```

---

## How to Use

- Use `examples/fixtures/` for authoritative runtime payloads
- Use `examples/projections/` for interoperability (JSON-LD)

IMM-native structures are authoritative.
JSON-LD projections are lossy and non-authoritative.

---

## Ontologies

This project aligns with:
- schema.org (exchange)
- PROV-O (provenance)
- FOAF, SKOS, ODRL, DCMI (optional semantics)

IMM semantics are never downgraded to fit an ontology.

---

## Status

This is a **living specification**.
Implementation is intentionally out of scope.


---

## Canon & ADR-0 Compatibility

Institutional Memory Model is a **derivative specification** aligned with the
System Momentum Canon and constrained by **ADR-0 (Epistemic Constraints)**.

- Canon and ADR-0 are authoritative.
- IMM operationalizes these constraints as enforceable structure.
- In case of conflict, Canon and ADR-0 prevail.

See: `governance/adr0-compatibility.md`
