# 01 — Evidence of relevance

**Status:** survey summary completed from the supplied Google Form results (n=20). Interviews with users or specialists have not been conducted.

## 1. Evidence overview and status

| Evidence item | Status / details |
|---------------|------------------|
| Google Form survey | Done; summary supplied for n=20. |
| Google Form URL | TODO: link not supplied. |
| Questionnaire | 14 items in Russian; version/date TODO. |
| Survey data export | Raw export location and export date TODO. |
| User/specialist interviews or discussions | NOT YET CONDUCTED. TODO: requirement asks for 3–5 discussions or a customer agreement. |
| Whether the survey satisfies the relevance-evidence requirement | Supervisor decision TODO. |

## 2. Survey method

The survey used a Google Form with 14 items in Russian. It was anonymous and included 18+ consent. Collection ran from 23 October 2026 at 16:55 to 24 October 2026 at 00:25. The sample was a non-probability convenience sample. Distribution channels, the form URL, questionnaire version, and raw-export location are TODO; they were not supplied with the summary.

## 3. Respondent profile

All counts below are from the supplied survey summary (n=20).

| Profile item | Responses |
|---------------|-----------|
| Age | 18–20: 16; 21–24: 3; declined: 1 |
| Occupation | Student: 13; employed: 3; self-employed: 2; not working: 1; declined: 1 |
| Medical education or work | Yes: 3 (1 with medical education, 2 working in medicine); no: 16; declined: 1 |

## 4. Results

### Recent skin concerns and information seeking

| Question area | Responses |
|---------------|-----------|
| Skin concerns in the last 12 months | Yes: 11; no: 7; unsure: 2 |
| Visited a dermatologist in the last 12 months | Yes: 5; no: 12; unsure: 3 |
| Searched for skin information in the last 12 months | Yes: 11; no: 7; unsure: 2 |
| Ways of finding information or help (multiple choice) | Search engines: 10; articles/medical sites: 7; doctor or clinic: 7; app or AI: 6; acquaintances or relatives: 6; social media/forums: 2 |
| Barriers to seeing a doctor (multiple choice) | Queue: 3; embarrassment: 2; problem judged not important enough: 2; cost: 1; distance: 1 |

### Prior use and willingness

| Question area | Responses |
|---------------|-----------|
| Prior use of apps/AI for skin or health | Skin and other health: 6; skin only: 3; other health only: 5; none: 5; do not remember: 1 |
| Willingness to use this type of app | Definitely ready: 9; rather ready: 5; rather not: 3; definitely not: 2; unsure: 1 |

### Trust and preferred app parameters

| Question area | Responses |
|---------------|-----------|
| Trust in AI preliminary assessment (1–5) | Rating 1: 1; 2: 1; 3: 8; 4: 6; 5: 4. Mean: 3.55. Ratings 4–5: 10 of 20. |
| Trust boosters (multiple choice) | Probability/confidence level: 8; description of photo processing: 8; plain-language explanation: 7; recommendation to see a dermatologist: 7; user reviews: 6; information about AI limitations: 5; information on quality verification: 5 |
| Free use | Mean importance: 4.05; ratings 4–5: 15 |
| Privacy of photos | Mean importance: 3.9; ratings 4–5: 12 |
| Accuracy | Mean importance: 3.8; ratings 4–5: 14 |
| Speed | Mean importance: 3.8; ratings 4–5: 12 |
| History of assessments | Mean importance: 3.7; ratings 4–5: 10 |
| Russian and Kazakh language support | Mean importance: 3.5; ratings 4–5: 12; rating 5: 9; rating 1: 5 |
| Offline operation | Mean importance: 2.45; ratings 4–5: 5; ratings 1–2: 10 of 20 |

### Payment, photo processing, and open responses

| Question area | Responses |
|---------------|-----------|
| Payment preference | Only free: 7; one-time up to 500 KZT: 2; one-time 501–1,500 KZT: 3; one-time over 1,500 KZT: 2; monthly up to 1,000 KZT: 2; monthly over 1,000 KZT: 2; unsure: 2 |
| Acceptable photo processing | Only on my device: 11; protected server with clear data-processing terms: 8; not willing to use a photo for this assessment: 1 |
| Fears in open responses (5 answers) | Data security: 1; confidentiality and distribution of data: 1; inaccurate assessment: 1; being judged: 1; nothing: 1 |

## 5. Findings and proposed requirement links

| Finding | Result | Interpretation | Proposed link to requirements |
|---------|--------|----------------|-------------------------------|
| F1 — Skin concerns and specialist visits | 55% reported skin concerns in the last 12 months; 25% reported a dermatologist visit. | In this sample, reported concerns were more common than dermatologist visits. This does not establish a population-level need or explain why visits differed. | FR-03 (preliminary analysis) and FR-06 (specialist referral) are relevant project features; the survey does not validate their effectiveness. |
| F2 — Self-help and barriers | Search engines were selected 10 times and articles/medical sites 7 times. Queue was selected as a barrier 3 times and embarrassment 2 times. | Respondents reported using online information and named several access barriers; the barrier counts are small. | No existing FR directly covers access barriers. Proposed: decide whether reliable next-step information needs a separate requirement; ID TODO. |
| F3 — Prior app/AI use | 45% reported prior app/AI use for skin. | Prior use is present in this sample but does not establish future behavior or trust. | No direct existing FR; contextual evidence only. Do not infer adoption. |
| F4 — Willingness and trust | 70% were definitely or rather ready to use such an app. Mean trust was 3.55/5; 10 of 20 rated trust 4–5. | Responses indicate interest alongside moderate trust in this sample. | FR-04 (class probabilities), FR-06 (referral), FR-07 (disclaimer), and NFR-05 (non-diagnostic wording). |
| F5 — Photo privacy | 55% (11 of 20) preferred processing only on their device; 40% (8 of 20) accepted a protected server with clear terms; 1 respondent was unwilling to use a photo. Offline operation had mean importance 2.45/5. | On-device processing is a privacy option to compare with server processing; the responses do not choose the architecture. Offline operation was rated lower in this sample (mean 2.45/5), which is a separate preference from photo-processing location. | FR-01 (consent), FR-02 (photo submission), FR-11 (deletion), and NFR-02 (data handling). Use the results as input to the server/on-device technology comparison, not as an architecture decision. |
| F6 — Trust boosters | Probability/confidence and a description of photo processing each received 8 selections; plain-language explanation and dermatologist recommendation each received 7; AI limitations and quality verification each received 5. | Respondents selected several kinds of information that could support informed use. | FR-04, FR-06, FR-07, and NFR-05 cover probabilities, referral, and disclaimer. No existing requirement explicitly covers a plain-language explanation or limitations screen. Proposed: consider whether to add one; ID TODO. |
| F7 — Feature priorities and languages | Free use had mean importance 4.05/5 (15 rated 4–5); accuracy 3.8 (14); speed 3.8 (12); privacy 3.9 (12); history 3.7 (10). The supplied summary characterizes history as Should. Language support had mean 3.5; 9 rated it 5 and 5 rated it 1. | The responses give mixed priorities. Language support ratings were split (9 rated it 5 and 5 rated it 1); they do not by themselves settle localization priority. | FR-05 (history), FR-08 (languages), NFR-01 (speed), NFR-02 (privacy), and NFR-04 (classification quality) are relevant. FR-05 is currently Must (draft), so reconcile that priority with the survey’s Should characterization. Free use has no existing FR; scope/price decision TODO. Localization priority decision TODO. |

## 6. Limitations

- The sample contains 20 respondents and uses non-probability convenience sampling.
- 16 of 20 respondents were aged 18–20; 13 were students; 3 reported medical education or work.
- Intentions and self-reports are not observed behavior.
- No specialist interviews or clinical validation of need have been conducted.
- The sample is not representative of the Kazakhstani population.
- Closed-answer options may have constrained responses.

## 7. Unvalidated assumptions

- The supplied responses do not establish population-level demand or predict actual use.
- Willingness to use the app does not establish trust in a real system or sustained use.
- Preferences for on-device processing or a protected server do not establish technical feasibility or a deployment choice.
- Survey responses do not validate model accuracy, clinical usefulness, or safety.
- Whether this survey satisfies the project’s relevance-evidence requirement remains for the supervisor to decide.
- Distribution channels and the exact questionnaire wording remain TODO.

## 8. Interviews

Interviews with users or specialists have **NOT YET BEEN CONDUCTED**. TODO: complete the requested 3–5 discussions or obtain a customer agreement, and ask the supervisor whether the survey counts toward the evidence requirement. Use the [interview instructions](interviews/README.md) and [interview note template](interviews/interview-note-template.md). No interview findings are reported here.

## 9. Appendix: question list

The supplied summary states that the form had 14 items but does not include their wording or short titles. Copy titles from the Google Form after its URL is available; do not infer them from the response categories.

| Item | Short title |
|------|-------------|
| 1 | TODO: exact title not supplied |
| 2 | TODO: exact title not supplied |
| 3 | TODO: exact title not supplied |
| 4 | TODO: exact title not supplied |
| 5 | TODO: exact title not supplied |
| 6 | TODO: exact title not supplied |
| 7 | TODO: exact title not supplied |
| 8 | TODO: exact title not supplied |
| 9 | TODO: exact title not supplied |
| 10 | TODO: exact title not supplied |
| 11 | TODO: exact title not supplied |
| 12 | TODO: exact title not supplied |
| 13 | TODO: exact title not supplied |
| 14 | TODO: exact title not supplied |
