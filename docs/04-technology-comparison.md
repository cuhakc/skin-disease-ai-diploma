# 04 — Technology comparison

**Status:** Decisions 1 and 5 have draft scores (Arman, 24 October 2026); Decisions 2–4 are still empty. Stack in the README is **proposed, pending this comparison**.

**Assessment use:** show alternatives, criteria, weighted scoring, and justification tied to requirement IDs (`docs/05-requirements-specification.md`).

## Instructions

1. Freeze requirement IDs before locking a choice.
2. Weights must sum to 1.0 per decision. Do not reverse-engineer scores to match a favourite.
3. Use a documented 1–5 scale (1 = least suitable, 5 = most suitable) unless the team agrees otherwise. Weighted total = sum of criterion weight multiplied by score.
4. Record the date and who scored. Disagreements go in notes.

**Proposed defaults (not chosen until tables are filled):** FastAPI, PostgreSQL, Flutter, PyTorch + TFLite/ONNX.

## Decision 1 — Model architecture

**Requirement IDs:** FR-03, FR-04, NFR-01, NFR-04.

**Scoring record:** draft scores by Arman, 24 October 2026, pending team review. Scale 1–5 (5 = most suitable). The criterion "accuracy on chosen dataset" is **not scored**: no baseline has been measured (TODO: measure, see `docs/08`). Add it, and re-score, after the first measured baseline.

| Criterion | Weight | Alt A: CNN, compact pretrained backbone (e.g. MobileNetV3 [4]) | Alt B: ViT / hybrid | Alt C: classical ML on handcrafted features |
|-----------|--------|------------------------------------------------------------|---------------------|-----------------------------------------------|
| Latency / model size on a phone (NFR-01) | 0.30 | 5 | 2 | 5 |
| Tooling: pretrained weights, mobile export | 0.20 | 5 | 3 | 3 |
| Literature support for skin classification | 0.30 | 5 | 3 | 2 |
| Explainability fit (FR-04, result screen) | 0.20 | 4 | 3 | 4 |
| **Weighted total** | 1.00 | **4.80** | **2.70** | **3.50** |
| Accuracy on chosen dataset | not scored | TODO: measure | TODO: measure | TODO: measure |

Rationale for scores:
- Latency / size: MobileNetV3 was designed and tuned for mobile CPUs [4]. Attention-based models add computational cost [13]. Handcrafted features are cheap to compute.
- Tooling: pretrained CNN weights and PyTorch to TFLite/ONNX export are mature (proposed defaults in the README); transformers are heavier to deploy; classical pipelines need hand-built feature code.
- Literature: CNNs are the dominant approach (over 70% of the papers in the survey [13]); see also [1], [10], [11]. Attention and transformers are covered but with the compute caveat [13]. Handcrafted-feature systems depend on feature quality and generalize poorly across datasets [13].
- Explainability: Grad-CAM was designed for CNNs [2], although its localization is coarse. Attention maps can be hard to interpret [13]. Classical features are interpretable but weak on multi-class tasks [13].

**Justification:** Alternative A has the highest draft total (4.80) and matches NFR-01 (response time, TODO target) and FR-04 (probabilities per class). The ranking is provisional: A must still reach acceptable recall on high-risk classes (NFR-04) in the measured baseline. Sensitivity check: if the latency weight is lowered to 0.10 and the literature weight raised to 0.50 (other weights unchanged), A stays first (4.80) and B and C tie (2.90 each), so only the winner is robust, not the order of B and C. TODO(Arman): recompute with the team's final weights.

## Decision 2 — Backend framework

**Requirement IDs:** FR-01, FR-02, FR-03, FR-05, FR-06, FR-07, NFR-01, NFR-02, NFR-03.

| Criterion | Weight | Alt A: FastAPI (proposed default) | Alt B: Django / Django REST | Alt C: Node.js (Nest/Express) |
|-----------|--------|-----------------------------------|-----------------------------|-------------------------------|
| TODO: time-to-OpenAPI | | | | |
| TODO: Python ML interop | | | | |
| TODO: team familiarity | | | | |
| TODO: async file upload | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Sultan): pending scoring.

## Decision 3 — Database

**Requirement IDs:** FR-05, NFR-02, NFR-03.

| Criterion | Weight | Alt A: PostgreSQL (proposed default) | Alt B: SQLite | Alt C: MongoDB |
|-----------|--------|--------------------------------------|---------------|----------------|
| TODO: relational integrity | | | | |
| TODO: ops / hosting | | | | |
| TODO: JSON for probabilities | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Sultan): pending scoring.

## Decision 4 — Mobile framework

**Requirement IDs:** FR-02, FR-08.

| Criterion | Weight | Alt A: Flutter (proposed default) | Alt B: React Native | Alt C: native Kotlin + Swift |
|-----------|--------|-----------------------------------|---------------------|------------------------------|
| TODO: one codebase | | | | |
| TODO: camera/gallery APIs | | | | |
| TODO: team skill | | | | |
| **Weighted total** | 1.00 | | | |

**Justification:** TODO(Amantai): pending scoring.

## Decision 5 — Model deployment (server vs on-device)

**Requirement IDs:** FR-02, FR-03, FR-04, NFR-01, NFR-02, NFR-03, NFR-04.

**Scoring record:** draft scores by Arman, 24 October 2026, pending review by Sultan (backend owner). Scale 1–5. Weights come from the survey (`docs/01`), not from preference: 11 of 20 respondents accepted only on-device processing, 8 of 20 accepted a protected server with clear terms, and photo privacy was rated 4–5 by 12 of 20 (F5). Offline operation had a mean of 2.45/5, so it gets a low weight.

| Criterion | Weight | Alt A: server-side inference | Alt B: on-device (TFLite/ONNX) | Alt C: hybrid (on-device by default, optional server with consent) |
|-----------|--------|------------------------------|--------------------------------|--------------------------------------------------------------------|
| Privacy of images (NFR-02) | 0.40 | 2 | 5 | 4 |
| Offline | 0.10 | 1 | 5 | 4 |
| Update model without store release | 0.20 | 5 | 2 | 4 |
| Device performance (NFR-01) | 0.30 | 5 | 2 | 3 |
| **Weighted total** | 1.00 | **3.40** | **3.50** | **3.70** |

Rationale for scores:
- Privacy: server inference sends every photo off the device; on-device keeps it; hybrid keeps it by default and sends only with consent.
- Offline: only on-device paths work without a connection.
- Updates: a server model changes instantly; an on-device model needs an app update or a model download.
- Device performance: a server removes the phone limit; on-device latency depends on the phone (TODO: measure on at least one mid-range phone).

**Justification:** Alternative C has the highest draft total (3.70), narrowly ahead of B (3.50) and A (3.40). The margin is small, so the choice rests on the survey privacy split and on measurements that do not exist yet: quality after compression, latency and model size on a phone (all TODO: measure). Implementation effort is not scored: a hybrid needs two inference paths, which Sultan should weigh in (TODO(Sultan)). Export formats TFLite/ONNX remain **proposed, pending this comparison**.

## Summary of locked choices

No technology has been selected by this document. Record each decision only after scoring and review.

| Decision | Choice | Date locked | Approved by |
|----------|--------|-------------|-------------|
| Model architecture | Draft: CNN family, compact backbone (candidate MobileNetV3 [4]); not locked | TODO | TODO |
| Backend framework | TODO | | |
| Database | TODO | | |
| Mobile framework | TODO | | |
| Deployment | Draft: hybrid, on-device by default; not locked | TODO | TODO |
