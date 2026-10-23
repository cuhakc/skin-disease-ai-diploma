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
