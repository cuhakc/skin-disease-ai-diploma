# 05 — Requirements specification

**Status:** draft requirements derived from the project brief and the confirmed RU/KK/EN language requirement. Review with the team and supervisor before treating these as approved.

**Assessment use:** FR/NFR with MoSCoW priority, measurable acceptance criteria, verification method, and owner.

## Instructions

- IDs use FR-xx and NFR-xx.
- Priorities are draft MoSCoW values.
- Keep thresholds marked to be confirmed until the team and supervisor agree on measurement conditions.
- Do not invent model accuracy, latency, or availability results.

## In-scope

Mobile photo capture/upload, authentication, preliminary classification request, result with class probabilities, history, specialist-referral recommendation, medical disclaimer, and application UI in RU/KK/EN. The class list is TODO(Arman).

## Out of scope

Definitive diagnosis, treatment or prescription advice, emergency triage, and clinical validation claims.

## Actors

| Actor | Description |
|-------|-------------|
| App user | Person who photographs/uploads a skin image and views a preliminary result |
| Specialist | Healthcare professional whom the user is advised to consult; no in-app specialist workflow is specified |
| System | Mobile application, API, and AI classification capability |

## Functional requirements

| ID | Description | Priority (MoSCoW) | Acceptance criterion (measurable) | Verification method | Owner |
|----|-------------|-------------------|-----------------------------------|---------------------|-------|
| FR-01 | The system shall support user registration and login. | Must (draft) | A new user can register; valid credentials authenticate; invalid credentials are rejected. | API and UI tests | Sultan |
| FR-02 | The app shall let a user capture or select and upload a skin photograph. | Must (draft) | A supported image can be submitted; unsupported types and files over the configured limit are rejected. Supported types and size limit: TODO(team), to be confirmed. | Mobile and API tests | Amantai / Sultan |
| FR-03 | The system shall accept an analysis request for an uploaded photograph. | Must (draft) | A valid request returns a preliminary result or a documented error; it is not represented as a diagnosis. | API integration test | Sultan / Arman |
| FR-04 | The result shall include a preliminary class label and class probabilities. | Must (draft) | The response contains one label and a numeric probability for each configured class; class list and output format: TODO(Arman). | Schema and service tests | Arman / Sultan |
| FR-05 | An authenticated user shall be able to view their analysis history. | Must (draft) | The user can list their own records; a different user cannot access those records. | API access-control tests | Sultan |
| FR-06 | Each analysis result shall include a recommendation to consult a specialist. | Must (draft) | Every returned result contains a non-empty specialist-referral recommendation. | API and UI checks | Sultan / Amantai |
| FR-07 | Diagnosis responses and result views shall include a medical disclaimer. | Must (draft) | Every diagnosis API response and result screen displays approved non-diagnostic wording; final wording: TODO(team). | API schema and UI checks | Sultan / Amantai |
| FR-08 | The application UI shall support Russian, Kazakh, and English. | Must (draft) | A user can select RU, KK, or EN and access the planned screens with reviewed translations in the selected language. Translation review: TODO(Amantai). | Locale-by-locale UI review | Amantai |

## Non-functional requirements

| ID | Description | Priority (MoSCoW) | Acceptance criterion (measurable) | Verification method | Owner |
|----|-------------|-------------------|-----------------------------------|---------------------|-------|
| NFR-01 | Analysis response time shall be measured against an agreed target. | Should (draft; target to be confirmed) | The 95th-percentile response time is at most TODO seconds under TODO device, network, image-size, and load conditions. | Timed evaluation under recorded conditions | Sultan / Arman |
| NFR-02 | Diagnosis records shall be protected from access by other users, and data handling shall be documented. | Must (draft) | Cross-user access checks deny access; documented data flows identify image and record storage, access, and retention decisions. | Access-control tests and design review | Sultan |
| NFR-03 | Service availability shall have an agreed target. | Should (draft; target to be confirmed) | Availability is measured over TODO observation window and compared with a target of TODO percent. | Availability measurement and report | Sultan |
| NFR-04 | Classification quality shall be evaluated against agreed thresholds. | Must (draft; thresholds to be confirmed) | Per-class precision, recall, F1, confusion matrix, and recall for classes designated high-risk are reported on a documented leakage-aware evaluation split; target values remain TODO. | Model evaluation report | Arman |
| NFR-05 | User-facing medical wording shall consistently communicate preliminary, non-diagnostic decision support. | Must (draft) | The approved disclaimer and specialist recommendation appear on every result view and diagnosis response in each supported language. | API and locale-by-locale UI review | Team |

## Traceability

| Requirement | Design artefact | Verification item |
|-------------|----------------|-------------------|
| FR-01 to FR-08 | Architecture and UX: TODO(team) | API/UI test plan in 08 |
| NFR-01 to NFR-05 | Architecture and evaluation plan: TODO(team) | Verification plan in 08 |

## Review and approval

| Reviewer | Date | Decision / changes |
|----------|------|-------------------|
| Team | TODO | TODO |
| Supervisor: Akerke Akanova | TODO | TODO |
