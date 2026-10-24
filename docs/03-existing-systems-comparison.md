# 03 — Existing systems comparison

**Status:** completed for pre-defence (24 October 2026). All cells are based on publicly available information as of 24 October 2026. Where information was not found, the cell contains “not stated”.

**Assessment use:** comparison of existing consumer-facing applications that analyse skin conditions from photographs against the intended capabilities of this diploma project.

## Systems under comparison

| Column | System name | Vendor / author | Platform | Source for identity |
|--------|-------------|-----------------|----------|---------------------|
| A | SkinVision | SkinVision B.V. | iOS, Android | https://www.skinvision.com |
| B | SkinScan (SkinScan AI) | Previously referenced in literature; current availability limited | Mobile (historical) | Freeman et al., BMJ 2020 [6] |
| C | Miiskin | Miiskin ApS | iOS, Android | https://miiskin.com |
| D | Aysa | Your.MD / Healthily | Web, iOS, Android | https://www.aysa.ai / https://www.healthily.com |
| E | Google DermAssist (DermAssist) | Google Health | Web (limited rollout) | https://health.google/health-research/dermassist/ |

This project (reference only): mobile photo → preliminary class probabilities + specialist recommendation + medical disclaimer. Not a diagnosis.

## Comparison criteria (10)

| ID | Criterion | How to score |
|----|-----------|--------------|
| C1 | Offline mode | yes / partial / no / not stated |
| C2 | Number / type of conditions | integer or description + source |
| C3 | Output type | class label / risk score / probabilities / other |
| C4 | History of past analyses | yes / no / not stated |
| C5 | Explicit recommendation to see a specialist | yes / no / not stated |
| C6 | Language support (RU / KK / EN) | list evidenced languages |
| C7 | Price model | free / freemium / subscription / one-time / not stated |
| C8 | Clinical validation evidence | published study / regulatory statement / not stated |
| C9 | Privacy / data handling of photos | summary + policy link or “not stated” |
| C10 | Medical disclaimer present | yes / no / not stated |

## Comparison matrix

| Criterion | SkinVision (A) | SkinScan (B) | Miiskin (C) | Aysa (D) | Google DermAssist (E) |
|-----------|----------------|--------------|-------------|----------|-----------------------|
| C1 Offline mode | no | not stated | no | no | no |
| C2 Number / type of conditions | Focus on skin cancer risk (melanoma and other lesions) | Skin cancer risk (historical) | Mole tracking + skin conditions | Multiple common skin conditions | 288 skin conditions (research version) |
| C3 Output type | Risk score (low/medium/high) | Risk assessment (historical) | Tracking + AI analysis | Condition suggestions | Ranked list of conditions |
| C4 History | yes (account required) | not stated | yes | yes | not stated |
| C5 Specialist recommendation | yes | not stated | yes (encourages professional check) | yes | yes (strongly recommends clinician) |
| C6 Languages (RU/KK/EN) | EN + several European; RU/KK not stated | not stated | EN + others; RU/KK not stated | EN + others; RU/KK not stated | EN primarily |
| C7 Price | Subscription / freemium | not stated (historical) | Free + premium subscription | Freemium | Research / limited access |
| C8 Clinical validation | Some published studies exist; systematic review (Freeman et al., 2020) concluded consumer apps cannot be relied on to detect all skin cancers | One small study reported 0% sensitivity for melanoma (Freeman et al., 2020) | Limited independent clinical validation found | Limited independent clinical validation found | Research papers by Google Health; not a general consumer diagnostic claim |
| C9 Privacy of photos | Policy available on website; photos processed on servers | not stated | Policy available; photos stored for tracking | Policy available | Google privacy policy; research context |
| C10 Medical disclaimer | yes | not stated | yes | yes | yes (strong non-diagnostic wording) |

**Sources used for the matrix (checked 24 October 2026):**
- SkinVision: https://www.skinvision.com and App Store / Google Play listings
- SkinScan: Freeman et al., BMJ 2020 (reference [6] in literature review)
- Miiskin: https://miiskin.com
- Aysa / Healthily: https://www.aysa.ai and https://www.healthily.com
- Google DermAssist: https://health.google/health-research/dermassist/
- Freeman et al. systematic review: BMJ 2020, doi: 10.1136/bmj.m127

## Gaps this project will address

Based only on the comparison above:

1. **Language support for the local context.** None of the compared systems clearly evidence Russian and Kazakh language support. This project explicitly targets RU / KK / EN.
2. **Transparent class probabilities.** Most existing apps provide a risk score or a short list of suggestions. This project plans to return class probabilities together with a specialist recommendation and a clear medical disclaimer.
3. **Explicit non-diagnostic positioning from the start.** All compared systems include some form of disclaimer, but the project documentation and UI will treat the output strictly as preliminary decision support.
4. **Open documentation of limitations.** The project will document dataset limitations, skin-tone considerations, and evaluation metrics rather than presenting only marketing claims.
5. **Traceable academic development process.** The diploma requires full traceability (Git + YouTrack + requirements + verification plan), which consumer apps do not provide.

No claim is made that the future system will be clinically superior. The gaps above are limited to features and documentation practices that are in scope for an engineering diploma project.