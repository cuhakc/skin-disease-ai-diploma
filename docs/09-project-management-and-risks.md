# 09 — Project management and risks

**Status:** process template. Dates and YouTrack URL are TODO. Do not invent burndown numbers.

**Assessment use:** Git + YouTrack, responsibilities, milestones, risks, dependencies.

## Tools

| Tool | Purpose | Link |
|------|---------|------|
| Git | source and review | this repository |
| YouTrack | tasks DIP-* | TODO(team): YouTrack URL |
| Pull requests | review | `.github/pull_request_template.md` |

## Branching (suggested)

`main` protected when remote exists. Feature branches `DIP-<n>-<slug>`. One YouTrack ID per PR where possible. **Do not share a single commit identity across students**—each person commits their own work.

## Responsibility matrix (draft)

| Area | Arman | Sultan | Amantai | Supervisor |
|------|-------|--------|---------|------------|
| Literature / ML quality | R | C | I | A |
| Backend / security | C | R | I | A |
| Mobile / UX | I | C | R | A |
| Docs (shared) | R | R | R | A |
| YouTrack hygiene | C | R | C | I |

R = responsible, A = accountable (supervisor for academic quality), C = consulted, I = informed.

## Milestones

| Milestone | Target date | Evidence |
|-----------|-------------|----------|
| Pre-defence 1 | 24 Oct (year TODO) | docs + diagrams + YouTrack |
| Requirements freeze | TODO | `05` signed off |
| Architecture freeze | TODO | `06` + diagrams |
| ML baseline | TODO | report, no fake metrics |
| API skeleton | TODO | OpenAPI |
| Mobile prototype | TODO | Figma + later app |
| Final defence | TODO | |

## Risk register

| Risk | Probability | Impact | Mitigation | Owner |
|------|-------------|--------|------------|-------|
| Data bias / shortage | TODO | TODO | licence-checked datasets; document limitations | Arman |
| Low accuracy | TODO | TODO | baseline, thresholds **to be confirmed**, no clinical overclaim | Arman |
| Ethics / legal (photos, health data) | TODO | TODO | disclaimer; minimise data; supervisor/legal TODO | Sultan + team |
| Integration (model ↔ API ↔ app) | TODO | TODO | mock inference first; contract tests | Sultan / Amantai |
| Schedule slip before pre-defence | TODO | TODO | docs-first; working app not required 24 Oct | team |

Add rows only for identified risks.

## Dependencies

| This work | Depends on | Status |
|-----------|------------|--------|
| Model training | dataset licence + split protocol | TODO |
| API diagnoses | inference interface | mock planned |
| Mobile upload | API contract | TODO |
| Relevance chapter | real sources / interviews | empty tables |

## YouTrack-ready task list

Full DIP-1… task breakdown (~25 tasks) is generated in **Phase 2**. Until then, track document ownership in meetings.

| ID | Title | Owner | Expected outcome | Acceptance criteria | Deadline | Priority |
|----|-------|-------|------------------|---------------------|----------|----------|
| DIP-1 | Repository skeleton | team | Phase 1 files | structure matches plan | TODO | Must |
