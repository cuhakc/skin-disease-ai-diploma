# 07 — UX prototype

**Status:** 5 screens described in text; Figma prototype not yet linked. **Do not invent a Figma URL or user-test results.**

**Assessment use:** prototype of the user journey (photo → result → specialist recommendation).

## Instructions

1. Link a real Figma/Penpot file when it exists.
2. Every result screen must show the medical disclaimer and that output is not a diagnosis.
3. Record accessibility notes (contrast, tap targets) without fake audit scores.

## Prototype link

TODO(Amantay): Figma (or other) URL

## Supported languages

The required UI languages are Russian (RU), Kazakh (KK), and English (EN). All screens below are described in English; translation text and review are TODO(Amantay).

## Intended screens (from project description)

| Screen | Purpose | Disclaimer visible | Notes / TODO |
|--------|---------|--------------------|--------------|
| Login / register with consent | Account for history, informed consent | short | Auth details TBD; consent wording TODO, legal review TODO |
| Camera / upload | Capture or pick a photo | short reminder | Reminder that the photo is sent for processing |
| Result | Preliminary class + probabilities | **required** | "See a specialist" **required** |
| History | Past analyses | required on detail | Per-user only |
| AI limitations help | Explain what the system can and cannot do | **required** | Not treatment advice |

## User flow (text)

1. Authenticate (if required by FR); on registration, give consent to data processing.
2. Capture or select a skin photo.
3. Confirm upload and processing (wording TODO, legal review TODO).
4. View preliminary classification and probabilities.
5. Read specialist recommendation and disclaimer.
6. Optionally open history or the AI limitations help.

## Screens

### Screen 1: Login / register with consent

**Purpose:** let the user sign in or create an account and give informed consent before any photo is processed.

**Elements:** email field, password field, "Sign in" button, "Create account" link; in registration mode a consent checkbox with a short text about how photos are processed and stored, and a link to the full privacy notice; short disclaimer: "This app provides a preliminary assessment, not a medical diagnosis."

**States:** empty form; validation error (invalid email or short password); consent not given (register button disabled); network error.

**Notes:** consent wording and data handling must match the backend security notes in docs/api/. Survey findings on privacy concerns are in docs/01-evidence-of-relevance.md. Legal review of the wording: TODO.

### Screen 2: Camera and upload

**Purpose:** capture or select a photo of the skin area.

**Elements:** camera preview, shutter button, gallery picker, short capture tips (good lighting, in focus, the area fills the frame), short reminder that the photo is sent for processing with a link to the privacy notice, "Continue" button after preview.

**States:** camera permission denied; photo too dark or blurry (warning); upload in progress; network error with retry.

### Screen 3: Result

**Purpose:** show a preliminary assessment with probabilities and clear limits.

**Elements:** submitted photo, list of top predicted classes with probabilities, short plain-language explanation, recommendation to consult a specialist, always-visible disclaimer: "This is not a diagnosis."

**States:** low-confidence result (stronger recommendation to see a specialist); image not recognised as skin; server error.

### Screen 4: History

**Purpose:** let the user review and delete previous assessments.

**Elements:** list of past results (date, thumbnail, top class), detail view with the disclaimer, delete action with confirmation.

**States:** empty history; loading; deletion failed.

**Notes:** history is per-user only.

### Screen 5: AI limitations help

**Purpose:** explain what the system can and cannot do.

**Elements:** list of supported classes (must match the scope in docs/00-project-proposal.md), known limitations (dataset coverage, skin tones, photo quality), how to interpret probabilities, when to seek urgent care, link to the privacy notice, disclaimer: "Not treatment advice and not a diagnosis."

## Prototype review log

| Date | Reviewer | Comments | Actions |
|------|----------|----------|---------|
| | | | |

## Usability evaluation

TODO: method (e.g. heuristic review). No fabricated task-success rates.