# 06 — Architecture

**Status:** placeholder. Editable diagram sources belong in `diagrams/source/` (Phase 3). Stack is **proposed, pending technology comparison**.

**Assessment use:** system context, use cases, components; diagrams with editable sources and exported images.

## Instructions

1. Keep diagrams consistent with `05-requirements-specification.md`.
2. Export PNG/SVG into `diagrams/exports/` (do not hand-draw undocumented boxes as the only source).
3. Note trust boundaries (phone, API, database, model).

## Proposed runtime (not final)

Mobile client → REST API → database; inference service (mock first, then model from `/ml`). Deployment of the model (server vs on-device) is **pending Decision 5** in `04-technology-comparison.md`.

## Diagrams

| Diagram | Source | Export | Status |
|---------|--------|--------|--------|
| System context | `diagrams/source/` (TODO Phase 3) | `diagrams/exports/` | not created |
| Use case | TODO | TODO | not created |
| Component | TODO | TODO | not created |

## Short description (fill after diagrams exist)

TODO(Sultan): components, data stores, auth, where images live, where probabilities are stored, how the disclaimer is attached to every result.

## Quality attributes

| Attribute | Approach (draft) | Requirement IDs |
|-----------|------------------|-----------------|
| Security | TODO | |
| Privacy | TODO | |
| Observability | TODO | |

## Open decisions

- Image storage: object store vs local disk — TODO
- Model interface — TODO
