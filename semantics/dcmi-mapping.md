# DCMI Mapping — Descriptive Metadata

## 1. Purpose

This document defines alignment between Institutional Memory Model (IMM)
and **Dublin Core (DCMI)** for descriptive metadata.

DCMI is used for **cataloging and discovery**, not reasoning.

---

## 2. Core Alignment

| IMM Concept | DCMI Property |
|------------|----------------|
| title      | dc:title       |
| description| dc:description |
| createdAt  | dc:created     |
| modifiedAt | dc:modified    |
| author     | dc:creator     |
| subject    | dc:subject     |

---

## 3. Mapping Rules

- DCMI MUST remain descriptive only.
- DCMI MUST NOT encode truth, validity, or verification.
- DCMI MAY be used for indexing and UI.

---

## 4. JSON-LD Example

```json
{
  "@context": {
    "dc": "http://purl.org/dc/elements/1.1/"
  },
  "@type": "dc:Dataset",
  "dc:title": "Decision Log",
  "dc:creator": "BrainAgent"
}
```
