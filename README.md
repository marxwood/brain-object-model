# Brain Object Model (BOM)

Brain Object Model (BOM) is a **specification-first epistemological model**
designed for AI agents and agentic systems.

Its purpose is to prevent epistemic collapse by strictly separating:
- assertions from verified knowledge,
- transient state from stable facts,
- reasoning from decision-making authority.

BOM is not a database schema, not an API, and not an ontology replacement.
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
brain-object-model/
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

BOM-native structures are authoritative.
JSON-LD projections are lossy and non-authoritative.

---

## Ontologies

This project aligns with:
- schema.org (exchange)
- PROV-O (provenance)
- FOAF, SKOS, ODRL, DCMI (optional semantics)

BOM semantics are never downgraded to fit an ontology.

---

## Status

This is a **living specification**.
Implementation is intentionally out of scope.
