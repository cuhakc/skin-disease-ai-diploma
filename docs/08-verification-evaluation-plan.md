# 08 — Verification and evaluation plan

**Status:** outline only. **No fake metrics.** Thresholds to be confirmed.

**Assessment use:** how the model, API, and UI will be checked (including leakage-aware splits and phone-photo evaluation).

## Instructions

Plan tests before implementation. Record datasets, split rules, and measurement conditions. Never paste unpublished “results”.

## Model evaluation (to be specified)

| Topic | Plan | Status |
|-------|------|--------|
| Metrics | accuracy; per-class precision/recall/F1; confusion matrix; recall for high-risk classes | thresholds TODO |
| Split | patient-level split to avoid lesion leakage | protocol TODO(Arman) |
| Phone photos | evaluation on real smartphone images (not only dermoscopy) | collection protocol TODO; ethics TODO |
| Baseline | simpler baseline vs chosen model | baseline TODO |
| High-risk classes | list TODO; recall target **to be confirmed** | |

## API / UI test plan (later)

| Area | What will be tested | Method |
|------|---------------------|--------|
| Auth | register/login | automated |
| Upload | type/size validation | automated |
| Access control | user A cannot read user B | automated |
| Disclaimer | present on diagnosis responses | automated + UI check |
| History | list/detail/delete | automated |

## Measurement conditions

TODO: device list, lighting, distance, image resolution, software versions. Empty until defined.

## Acceptance for diploma (software)

TODO(team): distinguish “works as decision support demo” from any clinical claim. Clinical validation is **out of scope** unless a sourced protocol exists.
