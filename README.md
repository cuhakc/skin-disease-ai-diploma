# Development of a Mobile Application for Disease Diagnosis Using AI Methods (Dermatological Pathologies)

Diploma project, Astana IT University (AITU), Software Engineering. A 3-person team is designing a mobile decision-support system: the user photographs skin, the system returns a **preliminary AI classification** and a **recommendation to consult a specialist**.

This is **not** a medical diagnosis and must never be presented as one.

## Short description

The intended product is a mobile client plus backend and an AI classification module for selected dermatological pathologies. The first pre-defence (24 October) requires analysis, design, planning, and supervision evidence—not a working application.

## Problem statement

TODO(team): Replace this with the problem statement agreed with the supervisor. Draft intent only: people may delay seeking care for skin lesions; a consumer tool that classifies a photo and always recommends specialist review is being investigated as **decision support**, not as a substitute for a clinician.

## Target users

TODO(team): Confirm personas with the supervisor. Intended primary users are adults using a smartphone camera. Intended secondary users may include clinicians reviewing exported history—**not confirmed**.

Out of scope until explicitly approved: paediatric use, emergency triage, and any claim of diagnosis or treatment.

## Expected outcomes

- Documented analysis: proposal, relevance, literature, existing systems, technologies.
- Requirements, architecture, UX prototype, and verification plan.
- Project management via Git and YouTrack.
- Later phases: AI module, REST API, and mobile client (not required for the first pre-defence).

## Team members and responsibilities

| Role | Name | Responsibility |
|------|------|----------------|
| Student 1 | Arman | AI module: dataset evaluation, model training, quality report |
| Student 2 | Sultan | Backend: architecture, REST API, database, security |
| Student 3 | Amantai | Mobile app: UI, photo capture/upload, API integration |
| Supervisor | TODO(team): supervisor full name, academic title, department | Scientific and organisational supervision |
| Additional members | TODO(team): if any | |

Student surnames and emails: TODO(team).

## Scope and current status

**In scope (diploma):** preliminary classification of a limited set of dermatological classes (class list TODO), photo capture/upload, result with probabilities, history, specialist-referral recommendation, medical disclaimer.

**Out of scope:** definitive diagnosis, prescription, telemedicine consultation, and unapproved clinical claims.

**Current status:** Phase 1 repository skeleton (analysis/design templates). Application code is not runnable yet.

**Pre-defence (24 Oct):** proposal, evidence of relevance, literature review, existing-system comparison, technology comparison, requirements, architecture diagrams (editable sources), UX prototype, verification plan, Git + YouTrack, supervisor feedback.

## Proposed technologies

The following are **proposed defaults only, pending technology comparison** (see `docs/04-technology-comparison.md`). Do not treat them as final:

| Area | Proposed default | Status |
|------|------------------|--------|
| Mobile | Flutter | proposed, pending technology comparison |
| Backend | FastAPI (Python 3.11+) | proposed, pending technology comparison |
| Database | PostgreSQL | proposed, pending technology comparison |
| ML training | PyTorch | proposed, pending technology comparison |
| On-device / export | TFLite and/or ONNX | proposed, pending technology comparison |

## Links

- YouTrack project: TODO(team): paste YouTrack URL
- Documentation index: [docs/](docs/)
- Architecture: [docs/06-architecture.md](docs/06-architecture.md)
- Diagrams: [diagrams/](diagrams/)

## Medical disclaimer

**This software is a research prototype for academic purposes. It does not provide medical diagnosis, treatment, or emergency advice.** Model output is a preliminary classification for decision support only. Users must consult a qualified healthcare professional. Do not delay seeking care because of an application result. The team does not assume clinical liability.

This disclaimer must appear in the product UI and in API responses when those exist.

## Setup

To be added when code is runnable.

Until then: copy `.env.example` to `.env` for local secrets (never commit `.env`).

## Run

To be added when code is runnable.

## Test

To be added when code is runnable.

## Repository layout

```
README.md
docs/          analysis and design (pre-defence)
diagrams/      editable sources and exports
backend/       API (later)
ml/            training and inference artefacts (later)
mobile/        client (later)
tests/         automated tests (later)
config/        shared configuration (later)
```
