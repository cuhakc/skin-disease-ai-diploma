# 05 — Requirements specification

**Status:** draft requirements derived from the project brief and the confirmed RU/KK/EN language requirement. Review with the team and supervisor before treating these as approved.

**Assessment use:** FR/NFR with MoSCoW priority, measurable acceptance criteria, verification method, and owner.

## Instructions

- IDs use FR-xx and NFR-xx.
- Priorities are draft MoSCoW values.
- Keep thresholds marked to be confirmed until the team and supervisor agree on measurement conditions.
- Do not invent model accuracy, latency, or availability results.

## In-scope

Mobile photo capture/upload, authentication, preliminary classification request, result with class probabilities, history, specialist-referral recommendation, medical disclaimer, and application UI in RU/KK/EN. The class catalogue endpoint is specified; supported taxonomy and risk-level values are TODO(Arman).

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
| FR-01 | The system shall support user registration and login with explicit data-processing consent. | Must (draft) | Registration requires explicit data-processing consent; the consent type, policy version, and grant timestamp are stored; registration with `consent_data_processing=false` is rejected with HTTP 422. Valid credentials authenticate; invalid credentials are rejected. | API tests for registration, consent persistence, false-consent rejection, and login | Sultan |
| FR-02 | The app shall let a user capture or select and upload a skin photograph. | Must (draft) | JPEG and PNG images can be submitted; the draft size limit is 10 MB (TODO confirm). Unsupported, over-limit, invalid, or unreadable images are rejected with a clear error (API draft: 415 for unsupported media type, 413 for over-limit, and 422 for invalid/unreadable input). | Mobile and API tests for accepted and rejected image inputs | Amantai / Sultan |
| FR-03 | The system shall accept an analysis request for an uploaded photograph. | Must (draft) | A valid request returns a preliminary result or a documented error; it is not represented as a diagnosis. | API integration test | Sultan / Arman |
| FR-04 | The result shall include a preliminary class label and class probabilities. | Must (draft) | The response contains one label and a numeric probability for each configured class; the class taxonomy remains TODO(Arman), and the response shape is defined in the API draft. | Schema and service tests | Arman / Sultan |
| FR-05 | An authenticated user shall be able to view their analysis history and a single record. | Must (draft) | The user can list only their own records and retrieve one of their own records using `GET /diagnoses/{id}`; a foreign or missing ID returns HTTP 404. | API access-control tests for list and detail operations | Sultan |
| FR-06 | Each analysis result shall include a recommendation to consult a specialist. | Must (draft) | Every returned result contains a non-empty specialist-referral recommendation. | API and UI checks | Sultan / Amantai |
| FR-07 | Diagnosis responses and result views shall include a medical disclaimer. | Must (draft) | Every diagnosis API response and result screen displays non-diagnostic wording; the English API draft uses `preliminary result, not a medical diagnosis`. Team review and translations remain TODO. | API schema and UI checks | Sultan / Amantai |
| FR-08 | The application UI shall support Russian, Kazakh, and English. | Must (draft) | A user can select RU, KK, or EN and access the planned screens with reviewed translations in the selected language. Translation review: TODO(Amantai). | Locale-by-locale UI review | Amantai |
| FR-09 | The client shall be able to retrieve the supported disease-class catalogue, including class names and risk level. | Must (draft) | `GET /classes` returns the configured classes with names in EN/RU/KK and a risk-level field; final taxonomy and risk-level vocabulary remain TODO. | API schema and catalogue review | Sultan |
| FR-10 | A user shall be able to read their profile. | Must (draft) | An authenticated user can retrieve their own profile through `GET /users/me`; an unauthenticated request is rejected with HTTP 401. | API authorization test | Sultan |
| FR-11 | A user shall be able to delete one diagnosis record or delete their account with all diagnosis records and images. | Must (draft) | The owner can delete one record and its image through `DELETE /diagnoses/{id}` or request account deletion through `DELETE /users/me`; the API returns HTTP 204 and deleted data is no longer accessible after the operation. Physical deletion timing remains TODO. | API authorization and storage integration tests for record and account deletion | Sultan |

## Non-functional requirements

| ID | Description | Priority (MoSCoW) | Acceptance criterion (measurable) | Verification method | Owner |
|----|-------------|-------------------|-----------------------------------|---------------------|-------|
| NFR-01 | Analysis response time shall be measured against an agreed target. | Should (draft; target to be confirmed) | The 95th-percentile response time is at most TODO seconds under TODO device, network, image-size, and load conditions. | Timed evaluation under recorded conditions | Sultan / Arman |
| NFR-02 | Diagnosis records shall be protected from access by other users, and data handling shall be documented. | Must (draft) | Cross-user access checks deny access; documented data flows identify image and record storage, access, and retention decisions. | Access-control tests and design review | Sultan |
| NFR-03 | `GET /health` shall provide the technical probe for service availability. | Should (draft; target and observation window to be confirmed) | The availability probe uses `GET /health`; availability is measured over TODO observation window and compared with target TODO. | Health-probe and availability measurement/report | Sultan |
| NFR-04 | Classification quality shall be evaluated against agreed thresholds. | Must (draft; thresholds to be confirmed) | Per-class precision, recall, F1, confusion matrix, and recall for classes designated high-risk are reported on a documented leakage-aware evaluation split; target values remain TODO. | Model evaluation report | Arman |
| NFR-05 | User-facing medical wording shall consistently communicate preliminary, non-diagnostic decision support. | Must (draft) | The approved disclaimer and specialist recommendation appear on every result view and diagnosis response in each supported language. | API and locale-by-locale UI review | Team |

## Traceability

| Requirement | Design artefact | Verification item |
|-------------|----------------|-------------------|
| FR-01 to FR-11 | Endpoint and design traceability in [06-architecture.md](06-architecture.md); UX details in 07 | API/UI test plan in 08 |
| NFR-01 to NFR-05 | Endpoint and design traceability in [06-architecture.md](06-architecture.md); evaluation plan in 08 | Verification plan in 08 |

## Review and approval

| Reviewer | Date | Decision / changes |
|----------|------|-------------------|
| Team | TODO | TODO |
| Supervisor: Akerke Akanova | TODO | TODO |
