# ML module

Owner: Arman.

Skeleton of the training and evaluation pipeline for preliminary classification of skin conditions from a photo. The product is decision support, **not a diagnosis**. This folder contains **no results**: every number must come from a logged experiment. Do not record fake metrics.

Related documents: `docs/04-technology-comparison.md` (Decisions 1 and 5), `docs/08-verification-evaluation-plan.md` (datasets, split, metrics, phone-photo check), `docs/05-requirements-specification.md` (FR-03, FR-04, NFR-01, NFR-04).

Proposed default (**pending technology comparison**): PyTorch; export TFLite and/or ONNX. Candidate backbone: MobileNetV3 [4] (draft choice in `docs/04`, not locked).

## Layout

```
ml/
├── README.md
├── notebooks/
│   └── 01_baseline.ipynb     # pipeline skeleton, no results
├── splits/                   # committed: patient-level split files (csv)
├── data/                     # NOT committed (root .gitignore): raw and processed images
├── checkpoints/              # NOT committed (root .gitignore)
└── weights/                  # NOT committed (root .gitignore)
```

## Datasets (references from `docs/02`)

| Ref | Dataset | Licence / terms | Status |
|-----|---------|-----------------|--------|
| [3] | HAM10000 | Non-commercial per the Harvard Dataverse page; exact licence TODO | Not downloaded |
| [7] | Fitzpatrick 17k | CC BY-NC-SA 3.0 (GitHub README); images come from original source URLs in the CSV | Not downloaded |
| [9] | DDI | TODO: check access terms | Not downloaded |

Datasets are not stored in Git. Check terms of use before any redistribution.

## Pipeline stages

1. **Data:** download [3], [7], [9]; record image type, classes, patient or lesion ID availability.
2. **Label mapping:** map labels to one class list (planned 5–10 classes). TODO(Arman): pending supervisor's answer (`docs/10`).
3. **Split:** patient-level train / validation / test, fixed seed, files in `splits/`. If no patient or lesion ID exists, document the limitation (`docs/08`).
4. **Preprocessing and augmentation:** resize, normalization, light augmentation. TODO: choose after inspecting the data.
5. **Model:** transfer learning from a compact pretrained CNN (draft hypothesis, to be confirmed by measurement).
6. **Training:** class-imbalance handling (weighted loss or resampling). TODO
7. **Evaluation:** per-class recall (high-risk classes first), specificity, precision, F1, AUROC with bootstrap CI over patients, confusion matrix, calibration; stratify by image source and skin tone where labels exist.
8. **Phone-photo check:** separate set, reported separately.
9. **Export and on-device measurement:** TFLite/ONNX size, latency, recall before and after compression. TODO: measure

## Setup

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install torch torchvision scikit-learn pandas numpy pillow jupyter
jupyter notebook ml/notebooks/01_baseline.ipynb
```

TODO: pin versions after the first successful run.

## Rules

- No fabricated results, metrics or screenshots.
- Test set used once per reported experiment.
- Each reported number records code commit, seed, split file and date.
- Do not commit images, weights or personal data.
