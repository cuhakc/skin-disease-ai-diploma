# 06 — Architecture

**Status:** draft diagrams created in Phase 3. Proposed technologies remain pending technology comparison.

**Assessment use:** system context, use cases, and a draft component view with editable sources and exported images.

## System overview

The project describes a mobile application that accepts a skin photograph, returns a preliminary AI classification with class probabilities, recommends consultation with a specialist, and presents a medical disclaimer. The draft component diagram separates the mobile app, API, authentication, diagnosis orchestration, inference interface, and persistence. It does not select a backend framework, database, image-storage mechanism, or inference deployment location.

## Architecture diagrams

| Diagram | Editable source | Export | Status |
|---------|-----------------|--------|--------|
| System context | [system-context.puml](../diagrams/source/system-context.puml) | [exports](../diagrams/exports/) | Draft source; export after PlantUML is available |
| Use case | [use-case.puml](../diagrams/source/use-case.puml) | [exports](../diagrams/exports/) | Draft source; export after PlantUML is available |
| Component | [component.puml](../diagrams/source/component.puml) | [exports](../diagrams/exports/) | Draft source; inference placement and storage are open decisions |

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
| Performance | Measure under documented device/network/load conditions | NFR-01 |
| Classification quality | Evaluate against agreed thresholds; no metrics recorded yet | NFR-04 |

## Open decisions

- Image storage and retention: TODO(Sultan).
- Inference deployment: server-side, on-device, or hybrid; compare in [04-technology-comparison.md](04-technology-comparison.md).
- Model interface and class taxonomy: TODO(Arman).
- Final technology choices: pending comparison.
