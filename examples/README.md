# Examples

This directory contains two **purpose-driven** sets of examples.

## 1) `fixtures/` — Runtime examples (authoritative)
These files are **Brain Object Model (BOM) native payloads** intended for:
- storage / APIs (e.g., `/brain/write`)
- test vectors / fixtures
- reference examples for implementation

They may include BOM-only semantics such as:
- validity leases
- verification traces (Claim → Fact)
- explicit conflict objects
- provenance fields

These files are **authoritative** examples of the BOM shape.

## 2) `projections/` — Interoperability examples (lossy)
These files are **JSON-LD interoperability projections** intended for:
- cross-system exchange
- SWD alignment (schema.org as lingua franca)
- provenance interoperability (PROV-O where applicable)

These are **lossy by design**:
- they must not be used to reconstruct full BOM semantics
- they do not encode validity leases, lifecycle, or full verification

### Quick rule
If you need to **execute** or **persist**: use `fixtures/`.
If you need to **share/align** across systems: use `projections/`.
