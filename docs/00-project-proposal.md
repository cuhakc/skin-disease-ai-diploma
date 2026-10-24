# 00 — Project proposal

**Status:** draft by Arman (24 October 2026) for team and supervisor review. Facts come only from `docs/01-evidence-of-relevance.md` (survey, n=20) and `docs/02-literature-review.md` (sources [1]–[14]). Unconfirmed items are marked `TODO(owner)`.

**Assessment use:** pre-defence proposal (problem, goal, object/subject, tasks, expected results, novelty/practical value as claimed by the team and confirmed by the supervisor).

## Title

Development of a Mobile Application for Disease Diagnosis Using AI Methods (Dermatological Pathologies)

Official Kazakh/Russian title (if required): TODO(team)

The product gives a preliminary assessment for decision support. It is **not** a medical diagnosis.

## Team and roles

| Role | Name | Responsibility |
|------|------|----------------|
| Student 1 | Arman | AI module: datasets, model, evaluation |
| Student 2 | Sultan | Backend: architecture, REST API, database, security |
| Student 3 | Amantai | Mobile app: UX, photo capture/upload, API integration |
| Supervisor | Akerke Akanova | Scientific and organisational supervision |

Surnames and emails: TODO(team). Student 3 is "Almukhammed" in the root `README.md` and "Amantai" in other docs: TODO(team) make consistent.

## Problem statement

People who notice a skin problem have few low-effort ways to decide whether to see a specialist. In the survey (n=20, convenience sample, adults 18+), 11 of 20 reported skin concerns in the last 12 months and 11 of 20 searched for information, while 5 of 20 saw a dermatologist (finding F1 in `docs/01`). Search engines (10 of 20) and articles (7 of 20) were the most common sources, and 9 of 20 had already used an app or AI for skin assessment (F2, F3).

Existing tools are a weak basis for that decision. A systematic review concluded that smartphone apps for skin-cancer risk cannot be relied on to detect all skin cancers [6]. In one teledermatology study, primary care physicians and nurse practitioners were less accurate than dermatologists (top-1 accuracy 0.44 and 0.40 versus 0.63) [5], which shows why decision support is attractive. Public datasets differ from ordinary phone photos [3], [7] and show weaker performance on dark skin tones [7], [9], so claims must be cautious.

The survey is exploratory: n=20, non-probability sample, 16 of 20 aged 18–20. It does not establish population-wide demand or clinical performance (limitations in `docs/01`).

## Target users

Adults who photograph a skin condition and want preliminary information and a recommendation about seeing a specialist. The survey population was adults 18+ (`docs/01`). Other age groups and any specialist workflow are not specified: TODO(team), supervisor to confirm.

## Goal

To design and prototype a mobile decision-support system in which a user photographs skin and receives a preliminary AI classification with class probabilities, a recommendation to consult a specialist, and a medical disclaimer. The system supports a decision and does not diagnose.

## Object and subject of study

Draft, TODO(supervisor): confirm wording.

- Object: preliminary assessment of skin conditions from photographs with mobile and AI technologies.
- Subject: image-classification methods, their evaluation on photographs, and the mobile/backend design that presents results as decision support.

## Tasks

| # | Task | Module | Owner | Status |
|---|------|--------|-------|--------|
| 1 | Choose model architecture and server vs on-device deployment with scored criteria (`docs/04`) | AI | Arman | Draft |
| 2 | Evaluate candidate datasets [3], [7], [9]; fix the class list (planned 5–10 classes, TODO(supervisor)) | AI | Arman | TODO |
| 3 | Build a reproducible training and evaluation pipeline with patient-level split (`ml/`, `docs/08`) | AI | Arman | Skeleton |
| 4 | Evaluate on smartphone photos, with recall for high-risk classes and skin-tone-stratified reporting (`docs/08`) | AI | Arman | Plan only |
| 5 | Design REST API, data model, authentication, consent and deletion (`docs/05`, `docs/06`, `docs/api/openapi.yaml`) | Backend | Sultan | TODO(Sultan) |
| 6 | Choose backend framework and database (`docs/04`) | Backend | Sultan | TODO(Sultan) |
| 7 | Design and prototype 5 screens in RU/KK/EN (`docs/07`) | Mobile | Amantai | TODO(Amantai) |
| 8 | Choose mobile framework (`docs/04`) | Mobile | Amantai | TODO(Amantai) |
| 9 | Compare with existing systems and record gaps (`docs/03`) | Team | Amantai | TODO(Amantai) |
| 10 | Collect supervisor feedback and stakeholder interviews (`docs/10`, `docs/interviews/`) | Team | All | TODO(team) |

## Expected results

Artefacts, without any claim of clinical validation:

- Analysis documents: proposal, evidence of relevance, literature review, existing-system comparison, technology comparison.
- Draft requirements, architecture diagrams, UX prototype, verification plan.
- A baseline ML pipeline and, after measurement, an evaluation report. Target metrics: TODO (they depend on the factors listed in `docs/08`).
- REST API specification and data model.
- Project-management evidence in Git and YouTrack.

## Novelty and practical value

TODO(supervisor): write only what the supervisor accepts. Candidate points to discuss, not claims: explicit evaluation on smartphone photos and by skin tone (motivated by [7], [9], [14]), and a privacy-aware deployment option (survey F5: 11 of 20 accepted only on-device processing).

## Scope

- **In scope:** preliminary classification of selected dermatological classes (planned 5–10, list TODO(Arman)), photo capture/upload, result with class probabilities, history, specialist-referral recommendation, medical disclaimer, authentication, RU/KK/EN UI.
- **Out of scope:** definitive diagnosis, prescription, telemedicine consultation, emergency triage, unapproved clinical claims.
- **Mandatory wording:** "preliminary assessment, not a medical diagnosis; consult a specialist".

## Constraints and ethics

- Medical disclaimer applies (see root `README.md`).
- Data protection: TODO(Sultan): legal basis for photos; applicability of Law 94-V to skin photographs is unchecked [12].
- Dataset licences: [3] HAM10000, non-commercial per the Harvard Dataverse page (see `docs/02`); [7] Fitzpatrick 17k, CC BY-NC-SA 3.0 per its GitHub README, with images fetched from original atlas URLs; [9] DDI, TODO(Arman). Non-commercial terms fit a diploma project but block commercial use.
- Class list: TODO(Arman), pending supervisor's answer in `docs/10`.

## Approval

| Item | Value |
|------|--------|
| Supervisor | Akerke Akanova |
| Date of approval | TODO |
| Pre-defence date | 24 October (year: confirm with department) |
