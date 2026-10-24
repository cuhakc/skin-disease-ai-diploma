# 02 — Literature review

**Status:** draft based only on the twelve source summaries supplied for this review. Full titles, author lists, publication details, and source locators not supplied are marked TODO.

**Assessment use:** review of dermatological image-classification methods and constraints relevant to a mobile decision-support application. This project does not present the output as a medical diagnosis.

## Scope and search note

The supplied source set is recorded as found through web searches on 24 October 2026. Sources were selected by topic relevance. No formal systematic search or screening protocol was used. The review is limited to references [1]–[12] and the facts supplied for them; no additional sources or bibliographic details have been added.

## Analysis table

| # | Citation (short) | Year | Type | Topic | Method/Data | Key result | Limitations | Relevance to project |
|---|-----------------|------|------|-------|-------------|------------|--------------|----------------------|
| 1 | Esteva et al. [1] | 2017 | scientific | CNN classification of skin-cancer images | One CNN trained end-to-end on a dermatologist-labelled dataset of 129,450 clinical images, including 3,374 dermoscopy images. | Performance was on par with the tested dermatologists on two skin-cancer tasks; the authors suggested mobile devices could extend dermatologists’ reach. | The tasks were limited to skin cancer. | Supports feasibility of image-based CNN classification and motivates considering mobile delivery. |
| 2 | Selvaraju et al. [2] | 2017 | scientific | Visual explanation of CNN predictions | Grad-CAM uses gradients flowing into the last convolutional layer to produce a coarse map of image regions important to a prediction; it does not require retraining. | Human studies indicated that the maps helped untrained users distinguish a stronger network from a weaker one. | Localization is coarse. | Candidate explainability method for a result screen and model debugging. |
| 3 | Tschandl, Rosendahl, and Kittler [3] | 2018 | scientific | HAM10000 dataset | 10,015 dermatoscopic images across 7 diagnostic categories of pigmented lesions; over 50% were pathology-confirmed; released for academic machine learning through the ISIC archive. | Provides a candidate dataset for model work. | Dermatoscopic images rather than smartphone photos; pigmented lesions only. Dataset terms must be checked; the supplied note says the Harvard Dataverse page states non-commercial use. | Candidate training dataset, subject to fit and terms-of-use review. |
| 4 | Howard et al. [4] | 2019 | scientific | MobileNetV3 for mobile inference | Architecture tuned to mobile phone CPUs using hardware-aware architecture search. | In the ICCV version, MobileNetV3-Large was reported as 3.2% more accurate than MobileNetV2 on ImageNet with 20% lower latency. | Results are from general image benchmarks, not dermatology. | Candidate lightweight backbone for on-device inference. |
| 5 | Liu et al. [5] | 2020 | scientific | Differential diagnosis from teledermatology cases | System used photographs plus clinical data from 16,114 cases; covered 26 common conditions (about 80% of primary-care cases) and a secondary prediction over 419 conditions. Validation used 963 cases. | Top-1 accuracy was 0.66 for the system, 0.63 for dermatologists, 0.44 for primary care physicians, and 0.40 for nurse practitioners. | Uses clinical metadata, not photos alone; one teledermatology source. | Informs consideration of ranked differential outputs and the specialist-shortage context. |
| 6 | Freeman et al. [6] | 2020 | scientific | Smartphone apps for skin-cancer risk | Systematic review of 9 diagnostic-accuracy studies of 6 apps. Clinicians selected lesions and acquired images rather than users. | In two studies (n=252), SkinVision sensitivity was 80% (95% CI 63–92) and specificity was 78% (67–87). One SkinScan study (n=15) reported 0% sensitivity for melanoma. The review concluded these apps cannot be relied on to detect all skin cancers. | Skin-cancer apps only; studies were small. | Supports cautious claims, a medical disclaimer, and referral recommendation. |
| 7 | Groh et al. [7] | 2021 | scientific | Fitzpatrick 17k dataset and skin-type performance | 16,577 clinical images from two dermatology atlases, with Fitzpatrick skin-type labels and 114 conditions. | The dataset contained far more light than dark skin images; a trained network was most accurate on skin types similar to its training data. | Images came from online atlases. | Candidate dataset and evidence to consider skin-tone bias. |
| 8 | WHO [8] | 2021 | other | Ethics and governance of AI for health | Institutional guidance dated 28 June 2021, organized around six principles. | Principles: protecting autonomy; promoting well-being, safety, and public interest; ensuring transparency, explainability, and intelligibility; fostering accountability; ensuring inclusiveness and equity; and promoting responsive and sustainable AI. | Guidance, not a legal act. | Informs ethical requirements for transparency, human oversight, and equity. |
| 9 | Daneshjou et al. [9] | 2022 | scientific | Diverse Dermatology Images (DDI) and performance across skin tones | Dataset of 656 pathologically confirmed images with diverse skin tones. | State-of-the-art dermatology AI models had ROC-AUC lower by 27–36% than in their original tests and performed worse on dark skin tones and uncommon diseases; fine-tuning on DDI closed the light/dark gap. | Small benchmark. | Supports evaluating performance on diverse skin tones. |
| 10 | Naqvi et al. [10] | 2023 | scientific | Deep learning for skin-cancer classification | Review of recent deep-learning work, common models, and datasets. | Provides an overview of models and datasets used in the reviewed work. | Focused on skin cancer. | Background for model and dataset selection. |
| 11 | Nugroho et al. [11] | 2024 | scientific | Deep learning on dermoscopic skin-lesion images | Systematic literature review describing preprocessing, segmentation, feature extraction, and classification. | Summarizes a pipeline used in the reviewed classification work. | Focused on dermoscopy. | Pipeline overview for the AI module. |
| 12 | Republic of Kazakhstan, Law No. 94-V [12] | 2013 (as amended; current-version date TODO) | other | Personal-data protection | Law regulating collection, processing, and protection of personal data. | The supplied summary states that storage period is determined by achievement of collection and processing purposes, and confidentiality of biometric data is set by legislation. | Applicability to skin photographs has not been assessed; legal check with supervisor is TODO. | Relevant to consent, retention, and deletion decisions. |

## Critical synthesis

(a) In the evaluated settings, the cited deep-learning systems reported strong comparisons with human practitioners: [1] reported performance on par with tested dermatologists on two skin-cancer tasks, and [5] reported a system top-1 accuracy of 0.66 on its validation cases, compared with 0.63 for dermatologists. These are study-specific findings, not results for this project [1], [5].

(b) The available datasets described here are not interchangeable with ordinary smartphone photos. HAM10000 contains dermatoscopic images of pigmented lesions [3], while Fitzpatrick 17k draws from online dermatology atlases [7]. DDI adds images with diverse skin tones but is a small benchmark [9].

(c) Representation and performance remain concerns: Fitzpatrick 17k has far more light than dark skin images, and its trained network performed best on skin types similar to its training data [7]. DDI evaluations also found lower ROC-AUC than the original tests, with worse results on dark skin tones and uncommon diseases [9].

(d) The smartphone-app review found that such apps cannot be relied on to detect all skin cancers [6]. Its findings support cautious, non-diagnostic wording and a recommendation to consult a specialist; they do not establish the performance of this project.

(e) Grad-CAM is a candidate way to show image regions relevant to a prediction, but its localization is coarse [2]. MobileNetV3 is a candidate mobile backbone based on general-image results, which do not establish dermatology performance [4].

(f) The WHO guidance supplies ethical principles for autonomy, safety, transparency, accountability, equity, and sustainability [8]. Kazakhstan’s personal-data law is relevant to collection, processing, retention, and confidentiality, but its applicability to skin photographs still requires a legal check [12].

## Gaps and positioning of this project

The project is positioned as preliminary decision support with class probabilities, a specialist-referral recommendation, and a medical disclaimer. Explainability and privacy-preserving deployment are options to evaluate, not demonstrated capabilities: Grad-CAM has coarse localization [2], and on-device versus server inference remains a project decision. No diagnostic-accuracy claim is made before the project’s own evaluation. The cited app review also cautions against relying on consumer apps to detect all skin cancers [6].

## Requirements check

- Source count: 12 total; 10 scientific sources ([1]–[7], [9]–[11]).
- Sources dated 2021 or later in the supplied set are [7]–[11]; [12] is the current amended legal text, but its current-version date is TODO. Of the 10 scientific sources, 4 ([7], [9]–[11]) are dated 2021 or later by the supplied year labels. Earlier scientific sources are foundational in this supplied set.
- TODO(team): add 2–3 scientific sources dated 2024–2026. Topic-owner proposals supplied: AI module topics — Arman; mobile/mHealth trust — Amantai; security/data protection — Sultan.
- Bibliographic titles, full author lists, publication details, and source locators were not supplied; verify them before final submission. No additional source has been added here.

## IEEE reference list

The supplied summary did not include full titles, author initials, volume/issue/page details, or persistent locators. These are left as TODO rather than inferred. Verify each entry before final submission. The numbering below matches the in-text citations and analysis table.

[1] Esteva et al., “Title: TODO,” *Nature*, 2017. Full author list, volume/issue/pages, DOI or URL: TODO.

[2] Selvaraju et al., “Title: TODO,” in *ICCV*, 2017. Full author list, pages, DOI or URL: TODO.

[3] Tschandl, Rosendahl, and Kittler, “Title: TODO,” *Sci. Data*, 2018. Full author initials, volume/pages, DOI or URL: TODO. Dataset-terms locator mentioned in the supplied summary: TODO.

[4] Howard et al., “Title: TODO,” in *ICCV*, 2019. Full author list, pages, DOI or URL: TODO.

[5] Liu et al., “Title: TODO,” *Nature Medicine*, 2020. Full author list, volume/issue/pages, DOI or URL: TODO.

[6] Freeman et al., “Title: TODO,” *BMJ*, 2020, systematic review. Full author list, volume/article details, DOI or URL: TODO.

[7] Groh et al., “Title: TODO,” in *CVPR Workshops*, 2021. Full author list, pages, DOI or URL: TODO.

[8] WHO, “Title: TODO,” institutional guidance, 28 June 2021. Official title and locator: TODO.

[9] Daneshjou et al., “Title: TODO,” *Science Advances*, 2022. Full author list, volume/issue/pages, DOI or URL: TODO.

[10] Naqvi et al., “Title: TODO,” *Diagnostics*, 2023, review. Full author list, volume/issue/article details, DOI or URL: TODO.

[11] Nugroho et al., “Title: TODO,” *Bull. Electr. Eng. Inform.*, 2024, systematic literature review. Full author list, volume/issue/pages, DOI or URL: TODO.

[12] Republic of Kazakhstan, Law No. 94-V, 21 May 2013, as amended. Official title, current text/version date, and official locator: TODO.

### Reading and verification owner proposal

| Reading / verification assignment | Owner | Status |
|-----------------------------------|-------|--------|
| Verify full metadata and relevance for existing references [1]–[12] | TODO | TODO |
| Additional AI module sources | Arman | TODO: confirm assignment and sources |
| Additional mobile/mHealth trust sources | Amantai | TODO: confirm assignment and sources |
| Additional security/data-protection sources | Sultan | TODO: confirm assignment and sources |

## Open questions

- Supported class taxonomy and risk vocabulary: TODO.
- Suitability and terms of use for candidate datasets: TODO.
- Whether candidate models and datasets transfer to smartphone photographs: TODO.
- Explainability method and on-device versus server inference: TODO.
- Legal applicability of the cited personal-data law to skin photographs: TODO: check with supervisor.
