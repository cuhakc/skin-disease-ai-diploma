# 09 — Project management and risks

**Status:** draft team plan. Dates and YouTrack URL remain TODO. The task table is prepared for YouTrack and has not been entered into the tracker.

**Assessment use:** Git and YouTrack workflow, responsibilities, milestones, risks, dependencies, and supervision evidence.

## Tools

| Tool | Purpose | Link / status |
|------|---------|---------------|
| Git | Source control and review | This repository |
| YouTrack | Project key DIP; Kanban board | Project URL TODO(team); tasks below are not yet created |
| Pull requests | Review | .github/pull_request_template.md |

## Branching and commits

Use task-based feature branches in the form DIP-<number>-<short-slug>. Each student commits under their own verified Git identity. No commits are made by this document update.

## Responsibility matrix (draft)

| Area | Arman | Sultan | Amantai | Supervisor |
|------|-------|--------|---------|------------|
| Literature / ML quality | R | C | I | A |
| Backend / security | C | R | I | A |
| Mobile / UX | I | C | R | A |
| Shared documentation | R | R | R | A |
| YouTrack hygiene | C | R | C | I |

R = responsible, A = accountable for academic oversight, C = consulted, I = informed. Confirm the matrix with the team and supervisor.

## Milestones

| Milestone | Target date | Evidence |
|-----------|-------------|----------|
| First pre-defence | 24 October; year to confirm | Analysis, design, planning, and supervision evidence |
| Requirements review | TODO(team) | Draft requirements reviewed |
| Architecture review | TODO(team) | Architecture description and editable diagrams reviewed |
| Literature and comparison review | TODO(team) | Verified sources and completed comparison tables |
| Model baseline | TODO(Arman) | Reproducible evaluation report; no results before measurement |
| API skeleton | TODO(Sultan) | API contract and implementation evidence |
| Mobile prototype | TODO(Amantai) | Prototype link and review record |
| Final defence | TODO(team) | Approved deliverables |

## Risk register

Probability and impact ratings are not assessed yet. Assign them during team review.

| Risk | Probability | Impact | Mitigation | Owner |
|------|-------------|--------|------------|-------|
| Dataset shortage or representation bias | TODO(team) | TODO(team) | Compare candidate datasets, inspect representation, check licences, and report limitations | Arman |
| Model accuracy is inadequate for intended decision support | TODO(team) | TODO(team) | Establish a baseline, use a leakage-aware evaluation plan, confirm thresholds, and avoid clinical claims | Arman |
| Ethics, privacy, or legal requirements for skin photos are unresolved | TODO(team) | TODO(team) | Confirm approvals and data handling with Akerke Akanova before collection or processing | Sultan / team |
| Integration problems between model, API, and mobile client | TODO(team) | TODO(team) | Agree API contract and integration checkpoints; use a mock inference interface first | Sultan / Amantai |
| Schedule slips before assessment milestones | TODO(team) | TODO(team) | Keep dates visible in Kanban, review dependencies regularly, and prioritize assessed deliverables | Team |

## Dependencies

| Work | Dependency | Owner / status |
|------|------------|----------------|
| Survey summary | Actual Google Form export, consent/notice review, and documented calculation method | Team; TODO |
| Relevance chapter | Survey summary and verified external sources | Arman; TODO |
| Model training | Class taxonomy, dataset access/licence review, and split protocol | Arman; TODO |
| Diagnosis API | Agreed requirements and inference interface | Sultan; mock interface planned |
| Mobile upload and result | Reviewed UX, API contract, and supported languages | Amantai / Sultan; TODO |
| Technology decision | Requirements, criteria, and evidence for alternatives | Team; TODO |
| Supervisor sign-off | Review time with Akerke Akanova | Team; TODO |

## YouTrack-ready task list

The rows below are draft task proposals for the DIP Kanban board, not existing YouTrack issues. Confirm owners, deadlines, and the priority mapping before creating them. DIP-1 owner is Sultan as specified.

| ID | Title | Owner | Expected outcome | Acceptance criteria | Deadline | Priority (draft) |
|----|-------|-------|------------------|---------------------|----------|------------------|
| DIP-1 | Repository baseline and DIP Kanban tracking setup | Sultan | Repository and task-tracking baseline | Repository documentation identifies the DIP Kanban board; project URL is recorded when available; branch and review workflow is documented | TODO | High |
| DIP-2 | Complete project proposal and scope | Team | Reviewed proposal draft | Goal, scope, users, constraints, and expected outcomes are documented; unsupported claims are marked TODO | TODO | High |
| DIP-3 | Record Google Form survey instrument and collection status | Amantai | Survey evidence metadata | Form link, version, collection status, population/sampling approach, consent status, and export location are recorded when known | TODO | High |
| DIP-4 | Summarize Google Form responses from the real export | Arman | Evidence summary based on actual responses | Every count and percentage is traceable to the export and calculation method; no invented responses; limitations are stated | TODO | High |
| DIP-5 | Gather verified external evidence of relevance | Arman | Source-backed relevance section | Each claim has a verified source, IEEE citation, locator, and access date where applicable | TODO | High |
| DIP-6 | Review literature on classification methods and datasets | Arman | Verified analysis-table entries | Sources are real, citations follow IEEE style, reported datasets/metrics match sources, and licensing questions are recorded | TODO | High |
| DIP-7 | Review literature on bias, explainability, mobile inference, and data protection | Arman | Verified analysis-table entries and synthesis | Relevant sources are verified; limitations and project relevance are separated from source claims | TODO | Normal |
| DIP-8 | Compare existing dermatology-related systems | Amantai | Source-linked system comparison | Three to five systems are identified; each filled feature cell has a source; unknowns are not guessed | TODO | High |
| DIP-9 | Compare candidate model architectures | Arman | Weighted model-architecture decision | Alternatives, criteria, weights totaling 1.0, evidence-based scores, requirement links, and rationale are recorded | TODO | High |
| DIP-10 | Compare backend framework and database alternatives | Sultan | Weighted backend/database decisions | Alternatives, criteria, weights totaling 1.0, evidence-based scores, requirement links, and rationale are recorded | TODO | High |
| DIP-11 | Compare mobile framework alternatives | Amantai | Weighted mobile-framework decision | Alternatives, criteria, weights totaling 1.0, evidence-based scores, requirement links, and rationale are recorded | TODO | Normal |
| DIP-12 | Compare server-side, on-device, and hybrid inference | Sultan | Deployment decision with ML input | Privacy, offline capability, latency, updates, and device constraints are scored with evidence and linked requirements | TODO | High |
| DIP-13 | Draft and review functional requirements | Team | FR table with owners and verification | Authentication, upload, analysis, result, history, referral, disclaimer, and RU/KK/EN support have IDs and measurable acceptance criteria | TODO | High |
| DIP-14 | Draft and review non-functional requirements | Sultan | NFR table with open thresholds explicit | Response time, data protection, availability, classification quality, and disclaimer consistency are specified; unapproved thresholds remain TODO | TODO | High |
| DIP-15 | Create UX prototype in RU, KK, and EN | Amantai | Linked prototype and screen flow | Login, photo capture/upload, result, history, and recommendation screens are present; disclaimer is visible; translations are reviewed | TODO | High |
| DIP-16 | Create editable architecture diagrams | Sultan | PlantUML source and exports | System context, use case, and draft component diagrams are editable and exportable to PNG/SVG; open decisions are marked | TODO | High |
| DIP-17 | Define ML verification and baseline protocol | Arman | Model evaluation protocol | Metrics, patient-level split, baseline, real-phone-photo conditions, and limitations are specified without fabricated results | TODO | High |
| DIP-18 | Define API, security, UI, and integration checks | Sultan | Requirement-linked verification plan | Authentication, upload validation, per-user access, history, result fields, disclaimer, language, and error cases map to verification methods | TODO | High |
| DIP-19 | Confirm survey and image data ethics/privacy process | Sultan | Documented data-handling questions and approvals | Consent, image storage, access, retention, and supervisor/ethics questions are documented before collecting or processing images | TODO | High |
| DIP-20 | Review project risks and dependencies with the team | Sultan | Updated risk register and dependency list | Probability, impact, mitigation, owner, and dependencies are reviewed and dated; unresolved values remain marked TODO | TODO | Normal |
| DIP-21 | Record supervisor feedback and actions | Team | Accurate supervisor feedback log | Actual feedback from Akerke Akanova is recorded or linked; each action has owner and status; no feedback is fabricated | TODO | High |
| DIP-22 | Evaluate dataset candidates and licences | Arman | Dataset selection note | Candidate datasets are labelled as candidates until reviewed; licence, suitability, and representation evidence are recorded | TODO | High |
| DIP-23 | Implement backend API skeleton after design review | Sultan | Backend implementation and API specification | Approved auth, upload, diagnosis, history, access-control, health, and disclaimer requirements are implemented and documented | TODO | Normal |
| DIP-24 | Implement mobile client and API integration after prototype review | Amantai | Mobile implementation | Approved screens support RU/KK/EN and integrate photo upload, result, disclaimer, recommendation, and history flows | TODO | Normal |
| DIP-25 | Assemble and review final diploma deliverables | Team | Final report and assessment package | Required documents, diagrams, prototype, verification evidence, project tracking, and supervisor feedback are linked and reviewed | TODO | High |

## Supervision and progress evidence

Supervisor: Akerke Akanova. Academic title, contact, meeting cadence, and feedback status: TODO(team). Record feedback only after it is received in [10-supervisor-feedback.md](10-supervisor-feedback.md).
