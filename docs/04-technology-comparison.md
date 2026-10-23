# 04 — Technology comparison

**Status:** decisions listed; **scores empty**. Stack in the README is **proposed, pending this comparison**.

**Assessment use:** show alternatives, criteria, weighted scoring, and justification tied to requirement IDs (`docs/05-requirements-specification.md`).

## Instructions

1. Freeze requirement IDs before locking a choice.
2. Weights must sum to 1.0 per decision. Do not reverse-engineer scores to match a favourite.
3. Record the date and who scored. Disagreements go in notes.

**Proposed defaults (not chosen until tables are filled):** FastAPI, PostgreSQL, Flutter, PyTorch + TFLite/ONNX.

## Decision 1 — Model architecture

**Requirement IDs:** TODO (e.g. FR for classification, NFR for accuracy/latency—IDs after `05` is drafted).

| Criterion | Weight | Alt A: CNN (e.g. family TBD) | Alt B: ViT / hybrid TBD | Alt C: classical ML on handcrafted features |
|-----------|--------|------------------------------|-------------------------|-----------------------------------------------|
| TODO: accuracy on chosen dataset | | | | |
| TODO: latency / size | | | | |
| TODO: tooling / team skill | | | | |
| TODO: literature support | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Arman): tie winner to requirement IDs. Pending scoring.

## Decision 2 — Backend framework

**Requirement IDs:** TODO (API, auth, OpenAPI).

| Criterion | Weight | Alt A: FastAPI (proposed default) | Alt B: Django / Django REST | Alt C: Node.js (Nest/Express) |
|-----------|--------|-----------------------------------|-----------------------------|-------------------------------|
| TODO: time-to-OpenAPI | | | | |
| TODO: Python ML interop | | | | |
| TODO: team familiarity | | | | |
| TODO: async file upload | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Sultan): pending scoring.

## Decision 3 — Database

**Requirement IDs:** TODO (persistence, history, access control).

| Criterion | Weight | Alt A: PostgreSQL (proposed default) | Alt B: SQLite | Alt C: MongoDB |
|-----------|--------|--------------------------------------|---------------|----------------|
| TODO: relational integrity | | | | |
| TODO: ops / hosting | | | | |
| TODO: JSON for probabilities | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Sultan): pending scoring.

## Decision 4 — Mobile framework

**Requirement IDs:** TODO (camera, upload, iOS/Android).

| Criterion | Weight | Alt A: Flutter (proposed default) | Alt B: React Native | Alt C: native Kotlin + Swift |
|-----------|--------|-----------------------------------|---------------------|------------------------------|
| TODO: one codebase | | | | |
| TODO: camera/gallery APIs | | | | |
| TODO: team skill | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Amantai): pending scoring.

## Decision 5 — Model deployment (server vs on-device)

**Requirement IDs:** TODO (latency, privacy, offline, model updates).

| Criterion | Weight | Alt A: server-side inference | Alt B: on-device (TFLite/ONNX) | Alt C: hybrid |
|-----------|--------|------------------------------|--------------------------------|---------------|
| TODO: privacy of images | | | | |
| TODO: offline | | | | |
| TODO: update model without store release | | | | |
| TODO: device performance | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Arman+Sultan): pending scoring. Export formats TFLite/ONNX remain **proposed, pending this comparison**.

## Summary of locked choices

| Decision | Choice | Date locked | Approved by |
|----------|--------|-------------|-------------|
| Model architecture | TODO | | |
| Backend framework | TODO | | |
| Database | TODO | | |
| Mobile framework | TODO | | |
| Deployment | TODO | | |
