# Development of a Mobile Application for Disease Diagnosis Using AI Methods (Dermatological Pathologies)

Diploma project, Astana IT University (AITU), Software Engineering. A three-person team is designing a mobile decision-support system: a person photographs skin, the system returns a preliminary AI classification and recommends consulting a specialist.

This is not a medical diagnosis.

## Short description

The intended product is a mobile application with a backend and an AI classification module for selected dermatological pathologies. The first pre-defence (24 October; year to confirm with the department) requires analysis, design, planning, and supervision evidence, not a working application.

## Problem statement

TODO(team): State the problem using evidence from the Google Form survey and verified sources. Do not present an assumed health-access problem or unreviewed survey response as a finding.

## Target users

The project is intended for people who photograph a skin condition and seek preliminary information from a mobile application. The system is expected to recommend consultation with a specialist. Age groups, clinical workflows, and any direct specialist access through the app are not yet specified.

TODO(team): Refine user groups only when supported by project evidence and supervisor review.

## Supported application languages

The planned application languages are Russian (RU), Kazakh (KK), and English (EN). Translation text and review are TODO(Amantai); do not present unreviewed translations as approved.

## Expected outcomes

- Documented analysis: proposal, evidence of relevance, literature review, existing-system comparison, and technology comparison.
- Draft requirements, architecture, UX prototype, and verification plan.
- Project management evidence using Git and a YouTrack Kanban board.
- Later project work: AI module, REST API, and mobile client.

TODO(team): Record implementation and evaluation outcomes only after the work has been completed and measured.

## Team members and responsibilities

| Role | Name | Responsibility |
|------|------|----------------|
| Student 1 | Arman | AI module: dataset evaluation, model training, quality report |
| Student 2 | Sultan | Backend: architecture, REST API, database, security |
| Student 3 | Almukhammed | Mobile app: UI, photo capture/upload, API integration |
| Supervisor | Akerke Akanova | Scientific and organisational supervision; academic title and contact TODO |

Student surnames and emails: TODO(team).

## Scope and current status

**In scope:** preliminary classification of selected dermatological classes (class list TODO), photo capture/upload, a result with class probabilities, history, specialist-referral recommendation, and medical disclaimer. Authentication and record ownership are included in the draft requirements.

**Out of scope:** definitive diagnosis, prescription, telemedicine consultation, and unapproved clinical claims.

**Current status:** Phase 2 documentation templates and Phase 3 editable PlantUML diagram sources are drafted. PNG/SVG exports await a PlantUML installation. Application code is not runnable.

**Pre-defence:** proposal, evidence of relevance, literature review, existing-system comparison, technology comparison, requirements, architecture diagrams, UX prototype, verification plan, Git and YouTrack, and supervisor feedback.

## Proposed technologies

The following are proposed defaults only, pending technology comparison:

| Area | Proposed default | Status |
|------|------------------|--------|
| Mobile | Flutter | proposed, pending technology comparison |
| Backend | FastAPI (Python 3.11+) | proposed, pending technology comparison |
| Database | PostgreSQL | proposed, pending technology comparison |
| ML training | PyTorch | proposed, pending technology comparison |
| On-device / export | TFLite and/or ONNX | proposed, pending technology comparison |

## Links

- YouTrack project key: DIP
- YouTrack board: Kanban
- YouTrack project URL: TODO(team)
- Documentation index: [docs/](docs/)
- Architecture: [docs/06-architecture.md](docs/06-architecture.md)
- Diagrams: [diagrams/](diagrams/)

## Medical disclaimer

**This software is intended for preliminary information and decision support only. It does not provide a medical diagnosis, treatment, or emergency advice.** Users should consult a qualified healthcare professional and should not delay seeking care because of an application result.

This disclaimer must appear in the product UI and in API diagnosis responses when those exist.

## Setup

To be added when code is runnable.

Until then, copy .env.example to .env for local secrets. Never commit .env.

## Run

To be added when code is runnable.

## Test

To be added when code is runnable.

## Repository layout

- docs/: analysis and design for pre-defence
- diagrams/: editable sources and exports
- backend/: API work
- ml/: training and inference work
- mobile/: client work
- tests/: automated tests
- config/: shared configuration
