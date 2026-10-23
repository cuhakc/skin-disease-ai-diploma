# 06 — Architecture

**Status:** draft diagrams created in Phase 3. Proposed technologies remain pending technology comparison.

**Assessment use:** system context, use cases, and a draft component view with editable sources and exported images.

## System overview

The project describes a mobile application that accepts a skin photograph, returns a preliminary AI classification with class probabilities, recommends consultation with a specialist, and presents a medical disclaimer. The draft component diagram separates the mobile app, API, authentication, consent storage, disease-class catalogue, diagnosis orchestration, inference interface, deletion flow, relational persistence, and image-file storage. It does not select a backend framework, database, image-storage mechanism, or inference deployment location.

## Architecture diagrams

| Diagram | Editable source | Export | Status |
|---------|-----------------|--------|--------|
| System context | [system-context.puml](../diagrams/source/system-context.puml) | [exports](../diagrams/exports/) | Draft source; export after PlantUML is available |
| Use case | [use-case.puml](../diagrams/source/use-case.puml) | [exports](../diagrams/exports/) | Draft source; export after PlantUML is available |
| Component | [component.puml](../diagrams/source/component.puml) | [exports](../diagrams/exports/) | Draft source; inference placement and storage are open decisions |
| Backend ER | [er-diagram.puml](../diagrams/source/er-diagram.puml) | [er-diagram.svg](../diagrams/exports/er-diagram.svg) | Draft source; SVG export pending PlantUML availability |

To export PNG and SVG files, see [diagrams/README.md](../diagrams/README.md). All diagram sources are editable PlantUML.

## Short description

The user captures or selects a photograph in the mobile app and requests preliminary analysis. The API boundary supports authentication, accepts the analysis request, and returns the preliminary label, class probabilities, specialist recommendation, and disclaimer. The diagnosis flow calls an inference interface and records history for the authenticated user. The inference implementation and persistence technology remain decisions to be compared.

TODO(Sultan): Confirm image storage, retention, access controls, and whether inference runs on the server or on-device.

## Trust boundaries and data handling

TODO(Sultan): Mark the mobile-to-API boundary, authentication boundary, image flow, persistence boundary, and any model boundary after the deployment decision. Do not imply a storage or retention policy that has not been agreed.

## Quality attributes

| Attribute | Draft approach | Requirement IDs |
|-----------|----------------|-----------------|
| Security | Per-user access control and secret handling; details TODO | NFR-02 |
| Privacy | Data flow, retention, and image storage decisions TODO | NFR-02 |
| Performance | Measure under documented device/network/load conditions; target and instrumentation TODO | NFR-01 |
| Availability | `/health` provides a basic health check; target, observation window, monitoring, and recovery behavior TODO | NFR-03 |
| Classification quality | Evaluate against agreed thresholds; no metrics recorded yet | NFR-04 |

## Open decisions

- Image storage and retention: TODO(Sultan).
- Inference deployment: server-side, on-device, or hybrid; compare in [04-technology-comparison.md](04-technology-comparison.md).
- Model interface and class taxonomy: TODO(Arman).
- Final technology choices: pending comparison.


## Backend API contract

The draft contract is [OpenAPI 3.0.3](api/openapi.yaml) (v0.1.0). It uses bearer JWT globally except for `/health` and `/auth/*`. The upload cap and several implementation policies remain draft/TODO.

## Requirement traceability (draft)

| Requirement | Endpoint or design element | Coverage / remaining partial item |
|-------------|----------------------------|-----------------------------------|
| FR-01 | `POST /auth/register`, `POST /auth/login`; `users` and `consents` in the ER model; consent row in security table | Partial: policy version value and persistence implementation are TODO. False consent is specified as HTTP 422. |
| FR-02 | [Mobile photo flow](07-ux-prototype.md); `POST /diagnoses` multipart upload | Partial: JPEG/PNG and draft 10 MB are specified; confirm size and unit. |
| FR-03 | `POST /diagnoses`; diagnosis orchestration and inference interface in component diagram | Partial: inference deployment and implementation remain TODO. |
| FR-04 | `POST /diagnoses` `Diagnosis` response; `DiseaseClass` schema and ER entity | Partial: final class taxonomy and output mapping remain TODO. |
| FR-05 | `GET /diagnoses`, `GET /diagnoses/{id}`; owner-only authorization and 404 behavior | Draft contract mapped; implementation and access-control verification remain pending. |
| FR-06 | `recommendation` in `Diagnosis`; specialist recommendation in UX | Partial: approved final recommendation wording and translations are TODO. |
| FR-07 | `disclaimer` in every `Diagnosis` response; result/disclaimer use case | Partial: approved user-facing translations and UI implementation remain TODO. |
| FR-08 | [RU/KK/EN UI support](07-ux-prototype.md); EN/RU/KK class names in `DiseaseClass` | Partial: reviewed translation content remains TODO. |
| FR-09 | `GET /classes`; disease-class catalogue component and `disease_classes` ER entity | Partial: taxonomy and risk-level vocabulary remain TODO. |
| FR-10 | `GET /users/me`; `User` response schema | Draft contract mapped; implementation and API verification remain pending. |
| FR-11 | `DELETE /diagnoses/{id}`, `DELETE /users/me`; deletion flow component and image-file storage | Partial: storage implementation and physical deletion timing remain TODO. |
| NFR-01 | [Timed measurement plan](08-verification-evaluation-plan.md); performance quality-attribute row | Partial: target, measurement conditions, and instrumentation remain TODO. |
| NFR-02 | Owner-only API access; backend security table; relational and image storage components | Partial: storage/hosting decisions, retention, and completed data-flow documentation remain TODO. |
| NFR-03 | `GET /health` technical probe; availability quality-attribute row | Partial: target, observation window, monitoring, and recovery behavior remain TODO. |
| NFR-04 | [Model evaluation plan](08-verification-evaluation-plan.md); `confidence`, `probabilities`, and `model_version` fields | Partial: class taxonomy, evaluation protocol, and thresholds remain TODO. |
| NFR-05 | `disclaimer` and `recommendation` in `Diagnosis`; localized result use cases | Partial: approved wording and translations remain TODO. |

Endpoint coverage check: `GET /health` → NFR-03; `POST /auth/register` and `POST /auth/login` → FR-01; `GET /users/me` → FR-10; `DELETE /users/me` → FR-11; `GET /classes` → FR-09; `POST /diagnoses` → FR-02, FR-03, FR-04, FR-06, FR-07, NFR-05; `GET /diagnoses` and `GET /diagnoses/{id}` → FR-05, FR-07, NFR-05; `DELETE /diagnoses/{id}` → FR-11.

## Backend security (draft)

| Area | Measure |
|------|---------|
| Authentication | Email and password; store password hashes using Argon2id or bcrypt; issue short-lived JWTs. Token lifetime is TODO. |
| Authorization | Enforce owner-only access to user data and diagnosis records; return 404 for foreign record IDs. |
| Transport | Use HTTPS in deployment, secure response headers, and restricted CORS. Deployment configuration is TODO. |
| Image upload | Whitelist JPEG/PNG MIME types, enforce the draft size limit, validate by decoding the image, generate random file names, and store files outside the web root. |
| Data minimisation | Do not require a legal name or medical history; strip EXIF and geolocation metadata from uploaded images. `display_name` is a user-selected display label. |
| User rights | Provide account deletion and deletion of a single diagnosis record, including associated images. Physical deletion timing is TODO. |
| Consent | Require explicit data-processing consent and store consent type, policy version, and grant timestamp; revocation handling is TODO. |
| Secrets | Read secrets from environment variables only; include placeholders, never real secrets, in `.env.example`. |
| Abuse protection | Apply rate limiting to login and image upload; thresholds and response behavior are TODO. |
| Logging | Do not log passwords, access tokens, or image contents. |
| Medical disclaimer | Include `preliminary result, not a medical diagnosis` in every diagnosis response. Keep the specialist recommendation as decision-support wording. |

### Open items

- Image retention period and physical deletion timing: TODO.
- Hosting location of personal data: TODO; check applicable Kazakhstan personal-data regulation before selecting a host.
- Final disease-class taxonomy: TODO; agree with the AI module owner and supervisor.
