# SHACL Constraints (Optional)

This folder contains **optional SHACL shapes** for machine-checkable validation of BOM graphs.

## What this is
- Structural validation of object types, required fields, and enums.
- A portability layer for implementations that already use RDF/JSON-LD pipelines.

## What this is not
- A truth engine.
- A replacement for BOM write-rules enforcement.
- A policy engine.

## Usage (typical)
- Load `bom-shapes.ttl` into your SHACL validator.
- Validate exported graphs or ingestion payloads before persistence.

## Notes
- Shapes are intentionally minimal (v0.1).
- Mode-specific constraints (e.g., `until_time` requires `expiresAt`) can be strengthened later with SHACL-SPARQL.
