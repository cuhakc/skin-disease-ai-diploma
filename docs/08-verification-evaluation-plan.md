# 08 — Verification and evaluation plan

**Status:** model-evaluation plan written (24 October 2026); API/UI plan unchanged. **No fake metrics.** Thresholds to be confirmed.

**Assessment use:** how the model, API, and UI will be checked (including leakage-aware splits and phone-photo evaluation).

## Instructions

Plan tests before implementation. Record datasets, split rules, and measurement conditions. Never paste unpublished “results”.

## Model evaluation

Updated by Arman, 24 October 2026. No results are reported. Numeric thresholds stay TODO; section "Threshold dependencies" lists what they depend on. Requirement link: NFR-04, FR-04.

### Datasets

| Ref | Dataset | Image type | Licence / terms | Patient or lesion ID | Skin-tone label | Role |
|-----|---------|-----------|-----------------|----------------------|-----------------|------|
| [3] | HAM10000 (10,015 images, 7 categories, pigmented lesions) | Dermatoscopic | Non-commercial per the Harvard Dataverse page (see `docs/02`); exact licence TODO(Arman) | TODO(Arman): confirm in the metadata file | No | Candidate training and evaluation data |
| [7] | Fitzpatrick 17k (16,577 images, 114 conditions) | Clinical, from two online atlases | CC BY-NC-SA 3.0 (GitHub README); images are downloaded from their original source URLs listed in the CSV | TODO(Arman): confirm | Yes (Fitzpatrick) | Candidate data and skin-tone-stratified evaluation |
| [9] | DDI (656 pathologically confirmed images, diverse skin tones) | Clinical | TODO(Arman): check access terms | TODO(Arman): confirm | Yes | Small benchmark for skin-tone evaluation, not for training volume |

Known mismatch: [3] is dermatoscopic and pigmented-lesion only, while users will upload ordinary phone photos [3], [7]. Reviews also report lower performance on smartphone images than in specialist settings, and lower performance on Fitzpatrick IV–VI [14]. The plan below is designed around these two risks.

### Plan

| Topic | Plan | Status |
|-------|------|--------|
| Class list | Map each dataset's labels to one project class list (planned 5–10 classes). Classes that cannot be mapped are excluded, not merged silently. | List TODO(Arman), pending supervisor (`docs/10`) |
| Metrics | Per-class recall (sensitivity), precision, F1; confusion matrix; macro and balanced accuracy; specificity for high-risk classes; AUROC per class (one-vs-rest) with bootstrap confidence intervals taken over patients; calibration (reliability curve, ECE) because probabilities are shown to the user (FR-04). Accuracy is never reported alone because of class imbalance. | Thresholds TODO |
| Primary metric | Recall for high-risk classes. A missed high-risk lesion is the costly error. Specificity is reported next to it to show the cost (unnecessary referrals). | High-risk list TODO(Arman) with supervisor or medical expert |
| Split | Patient-level split into train, validation and test: all images of a patient go to one subset. If a dataset has no patient ID, use the lesion ID. If it has neither, the leak-free guarantee is impossible: state this as a limitation and label that dataset's test numbers accordingly. Split first, merge datasets after. Fixed seed; split files stored in the repository. | Protocol written; apply when data is downloaded |
| Test discipline | Test set used once per reported experiment; hyperparameters chosen on validation only. Every reported number records code commit, seed, split file and date. | Rule |
| Baseline | A simple baseline (for example a linear classifier on features of a frozen pretrained backbone) is compared with the fine-tuned compact CNN chosen in `docs/04`, to show what fine-tuning adds. | Baseline definition TODO |
| Class imbalance | Report per-class numbers; use weighted loss or resampling and say which. | TODO |
| Phone photos | Evaluate the final model on a separate set of real smartphone photos and report it separately from the benchmark test. Source of images: TODO (public clinical or phone-photo data, or volunteers with written consent). No photos of identifiable people are stored; no data from minors. Also measure how many photos the app rejects for blur, lighting or distance (TODO: measure). | Collection protocol and ethics TODO |
| Skin-tone reporting | Report metrics by Fitzpatrick group where labels exist ([7], [9]); at least I–III versus IV–VI, as in [14]. | Planned |
| On-device measurements | Model size, latency on at least one mid-range phone, and recall before and after compression (links to deployment decision in `docs/04`). | TODO: measure |
| Explainability check | If Grad-CAM [2] is shown on the result screen, check on a sample of images that highlighted regions are on the lesion, and report failures. | Planned |

### Threshold dependencies

No numeric target is fixed. The recall threshold for high-risk classes and the decision threshold for the "see a specialist" recommendation depend on:

1. Intended use: decision support and referral, not diagnosis, which favours recall over precision.
2. Cost of a missed high-risk lesion versus an unnecessary referral. This is a clinical judgement to agree with the supervisor or a medical expert, not a technical one.
3. Class prevalence in the training data versus the real user population.
4. The class list and which classes count as high-risk.
5. Literature context, not targets: unreliable results of consumer apps [6], and the gap between smartphone and specialist settings [14].
6. What the model reaches on the phone-photo set, not only on the benchmark test set.
7. Calibration quality, because probabilities are shown.
8. Quality loss from on-device compression.

TODO(team): fix numbers after the first measured baseline and the supervisor's reply.

## API / UI test plan (later)

| Area | What will be tested | Method |
|------|---------------------|--------|
| Auth and consent | Register/login; persist consent type, policy version, and grant timestamp; reject false consent with HTTP 422 | Automated API and storage tests |
| Upload | JPEG/PNG; draft 10 MB limit (TODO confirm); clear errors for unsupported, over-limit, invalid, or unreadable images | Automated API tests |
| Access control | User A cannot read user B history or detail; foreign or missing record IDs return 404 | Automated API tests |
| Class catalogue | `GET /classes` returns configured names and risk level; taxonomy and risk vocabulary remain TODO | API schema and integration review |
| Profile | `GET /users/me` returns the authenticated user's profile; unauthenticated request returns 401 | Automated API tests |
| History | List and retrieve only the authenticated user's records | Automated API tests |
| Deletion | `DELETE /diagnoses/{id}` and `DELETE /users/me` make the associated records and images inaccessible; physical deletion timing TODO | API and storage integration tests |
| Health | `GET /health` is the technical availability probe; target and observation window TODO | Probe check and availability measurement |
| Disclaimer | Present on every diagnosis API response and result screen | Automated API test and UI check |

## Measurement conditions

TODO: device list, lighting, distance, image resolution, software versions. Empty until defined.

## Acceptance for diploma (software)

TODO(team): distinguish “works as decision support demo” from any clinical claim. Clinical validation is **out of scope** unless a sourced protocol exists.
