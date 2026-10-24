# 02 — Literature review

**Status:** first complete draft; 12 sources verified against publisher or repository pages on 24 October 2026, and two AI-module sources ([13], [14]) added and checked against their publisher or PMC pages on the same date. Remaining TODOs: sources from Amantai (mHealth/trust) and Sultan (data protection), legal check of Law 94-V, and a final read-through of the table against the sources.

**Assessment use:** review of dermatological image-classification methods and constraints relevant to a mobile decision-support application. This project does not present the output as a medical diagnosis.

## Scope and search note

Sources were found through web searches on 24 October 2026 and selected by topic relevance, without a formal systematic protocol. The review is limited to references [1]–[14].

## Analysis table

| # | Citation (short) | Year | Type | Topic | Method/Data | Key result | Limitations | Relevance to project |
|---|-----------------|------|------|-------|-------------|------------|--------------|----------------------|
| 1 | Esteva et al. [1] | 2017 | scientific | CNN classification of skin-cancer images | One CNN trained end-to-end on a dermatologist-labelled dataset of 129,450 clinical images, including 3,374 dermoscopy images. | Performance was on par with the tested dermatologists on two skin-cancer tasks; the authors suggested mobile devices could extend dermatologists’ reach. | The tasks were limited to skin cancer. | Supports feasibility of image-based CNN classification and motivates considering mobile delivery. |
| 2 | Selvaraju et al. [2] | 2017 | scientific | Visual explanation of CNN predictions | Grad-CAM uses gradients flowing into the last convolutional layer to produce a coarse map of image regions important to a prediction; it does not require retraining. | Human studies indicated that the maps helped untrained users distinguish a stronger network from a weaker one. | Localization is coarse. | Candidate explainability method for a result screen and model debugging. |
| 3 | Tschandl, Rosendahl, and Kittler [3] | 2018 | scientific | HAM10000 dataset | 10,015 dermatoscopic images across 7 diagnostic categories of pigmented lesions; over 50% were pathology-confirmed; released for academic machine learning through the ISIC archive. | Provides a candidate dataset for model work. | Dermatoscopic images rather than smartphone photos; pigmented lesions only. Dataset terms must be checked; the Harvard Dataverse page states non-commercial use. | Candidate training dataset, subject to fit and terms-of-use review. |
| 4 | Howard et al. [4] | 2019 | scientific | MobileNetV3 for mobile inference | Architecture tuned to mobile phone CPUs using hardware-aware architecture search. | In the ICCV version, MobileNetV3-Large was reported as 3.2% more accurate than MobileNetV2 on ImageNet with 20% lower latency. | Results are from general image benchmarks, not dermatology. | Candidate lightweight backbone for on-device inference. |
| 5 | Liu et al. [5] | 2020 | scientific | Differential diagnosis from teledermatology cases | System used photographs plus clinical data from 16,114 cases; covered 26 common conditions (about 80% of primary-care cases) and a secondary prediction over 419 conditions. Validation used 963 cases. | Top-1 accuracy was 0.66 for the system, 0.63 for dermatologists, 0.44 for primary care physicians, and 0.40 for nurse practitioners. | Uses clinical metadata, not photos alone; one teledermatology source. | Informs consideration of ranked differential outputs and the specialist-shortage context. |
| 6 | Freeman et al. [6] | 2020 | scientific | Smartphone apps for skin-cancer risk | Systematic review of 9 diagnostic-accuracy studies of 6 apps. Clinicians selected lesions and acquired images rather than users. | In two studies (n=252), SkinVision sensitivity was 80% (95% CI 63–92) and specificity was 78% (67–87). One SkinScan study (n=15) reported 0% sensitivity for melanoma. The review concluded these apps cannot be relied on to detect all skin cancers. | Skin-cancer apps only; studies were small. | Supports cautious claims, a medical disclaimer, and referral recommendation. |
| 7 | Groh et al. [7] | 2021 | scientific | Fitzpatrick 17k dataset and skin-type performance | 16,577 clinical images from two dermatology atlases, with Fitzpatrick skin-type labels and 114 conditions. | The dataset contained far more light than dark skin images; a trained network was most accurate on skin types similar to its training data. | Images came from online atlases. | Candidate dataset and evidence to consider skin-tone bias. |
| 8 | WHO [8] | 2021 | other | Ethics and governance of AI for health | Institutional guidance dated 28 June 2021, organized around six principles. | Principles: protecting autonomy; promoting well-being, safety, and public interest; ensuring transparency, explainability, and intelligibility; fostering accountability; ensuring inclusiveness and equity; and promoting responsive and sustainable AI. | Guidance, not a legal act. | Informs ethical requirements for transparency, human oversight, and equity. |
| 9 | Daneshjou et al. [9] | 2022 | scientific | Diverse Dermatology Images (DDI) and performance across skin tones | Dataset of 656 pathologically confirmed images with diverse skin tones. | State-of-the-art dermatology AI models had ROC-AUC lower by 27–36% than in their original tests and performed worse on dark skin tones and uncommon diseases; fine-tuning on DDI closed the light/dark gap. | Small benchmark. | Supports evaluating performance on diverse skin tones. |
| 10 | Naqvi et al. [10] | 2023 | scientific | Deep learning for skin-cancer classification | Review of recent deep-learning work, common models, and datasets. | Provides an overview of models and datasets used in the reviewed work. | Focused on skin cancer. | Background for model and dataset selection. |
| 11 | Nugroho et al. [11] | 2024 | scientific | Deep learning on dermoscopic skin-lesion images | Systematic literature review describing preprocessing, segmentation, feature extraction, and classification. | Summarizes a pipeline used in the reviewed classification work. | Focused on dermoscopy. | Pipeline overview for the AI module. |
| 12 | Republic of Kazakhstan, Law No. 94-V [12] | 2013 (as amended) | other | Personal-data protection | Law regulating collection, processing, and protection of personal data. | The law states that the storage period is determined by achievement of the purposes of collection and processing, and that confidentiality of biometric data is set by legislation. | Applicability to skin photographs has not been assessed; legal check with supervisor is TODO. | Relevant to consent, retention, and deletion decisions. |
| 13 | Ray, Sarkar, Schwenker, and Sarkar [13] | 2024 | scientific | Survey of skin-cancer classification methods | Survey of 107 papers over 18 years: datasets (HAM10000, ISIC archive and others), classical ML, CNNs, transfer learning, attention, ensembles, transformers, hybrid and multimodal methods. | CNN-based papers made up over 70% of the surveyed deep-learning work. The survey notes that pretrained natural-image models face a domain shift on dermoscopic images, so fine-tuning is needed, and that attention-based models add computational cost. Handcrafted-feature systems depend on feature quality and generalize poorly across datasets. | A survey: no experiments of its own; dermoscopy and skin cancer focus. | Supports the choice of a fine-tuned CNN, informs dataset limits and the compute trade-off (`docs/04`, `docs/08`). |
| 14 | Tjiu and Lu [14] | 2025 | scientific | Equity and generalizability of dermatology AI | Systematic review and meta-analysis of 18 studies (clinical, dermoscopic and smartphone images), search up to 31 October 2025. | Pooled AUROC was 0.88. By setting, AUROC was 0.90 in specialist, 0.85 in community and 0.81 in smartphone environments. By skin tone, AUROC was 0.89 for Fitzpatrick I–III and 0.82 for IV–VI. The authors call for diverse data, skin-tone-stratified reporting and external validation. | Single-source MDPI review; only 6 of 18 studies had complete 2×2 data; heterogeneous settings. Cite headline findings only. | Motivates the phone-photo check and skin-tone-stratified reporting in `docs/08` and cautious wording in `docs/00`. |

## Critical synthesis

(a) In the evaluated settings, the cited deep-learning systems reported strong comparisons with human practitioners: [1] reported performance on par with tested dermatologists on two skin-cancer tasks, and [5] reported a system top-1 accuracy of 0.66 on its validation cases, compared with 0.63 for dermatologists. These are study-specific findings, not results for this project [1], [5].

(b) The available datasets described here are not interchangeable with ordinary smartphone photos. HAM10000 contains dermatoscopic images of pigmented lesions [3], while Fitzpatrick 17k draws from online dermatology atlases [7]. DDI adds images with diverse skin tones but is a small benchmark [9].

(c) Representation and performance remain concerns: Fitzpatrick 17k has far more light than dark skin images, and its trained network performed best on skin types similar to its training data [7]. DDI evaluations also found lower ROC-AUC than the original tests, with worse results on dark skin tones and uncommon diseases [9].

(d) The smartphone-app review found that such apps cannot be relied on to detect all skin cancers [6]. Its findings support cautious, non-diagnostic wording and a recommendation to consult a specialist; they do not establish the performance of this project.

(e) Grad-CAM is a candidate way to show image regions relevant to a prediction, but its localization is coarse [2]. MobileNetV3 is a candidate mobile backbone based on general-image results, which do not establish dermatology performance [4].

(f) The WHO guidance supplies ethical principles for autonomy, safety, transparency, accountability, equity, and sustainability [8]. Kazakhstan’s personal-data law is relevant to collection, processing, retention, and confidentiality, but its applicability to skin photographs still requires a legal check [12].

(g) Two 2024–2025 reviews add to this picture. A survey of 107 papers reports that CNNs dominate skin-lesion classification, that pretrained natural-image models need fine-tuning because of domain shift, and that attention-based models add computation [13]. A meta-analysis of 18 studies reports lower AUROC in smartphone settings (0.81) than in specialist settings (0.90) and lower AUROC for Fitzpatrick IV–VI (0.82) than for I–III (0.89) [14]. Both support a fine-tuned compact CNN as a baseline to be tested, and an explicit evaluation on phone photos and by skin tone. Neither establishes the performance of this project.

## Gaps and positioning of this project

The project is positioned as preliminary decision support with class probabilities, a specialist-referral recommendation, and a medical disclaimer. Explainability and privacy-preserving deployment are options to evaluate, not demonstrated capabilities: Grad-CAM has coarse localization [2], and on-device versus server inference remains a project decision. No diagnostic-accuracy claim is made before the project’s own evaluation. The cited app review also cautions against relying on consumer apps to detect all skin cancers [6].

## Requirements check

- Source count: 14 total; 12 scientific sources ([1]–[7], [9]–[11], [13], [14]).
- Sources dated 2021 or later are [7]–[11], [13] and [14]; [12] is the current amended legal text, but its current-version date is TODO. Of the 12 scientific sources, 6 ([7], [9]–[11], [13], [14]) are dated 2021 or later by the year labels. Earlier scientific sources are foundational.
- Scientific sources dated 2024–2026: [11], [13], [14]. The AI-module sources are added ([13], [14] by Arman). TODO(Amantai): 1–2 mobile/mHealth trust sources (numbers from [15]). TODO(Sultan): security/data-protection sources.
- All 12 references have a DOI or an official URL; volume and page details are given where the publisher provides them.

## IEEE reference list

[1] A. Esteva et al., "Dermatologist-level classification of skin cancer with deep neural networks," Nature, vol. 542, no. 7639, pp. 115–118, 2017, doi: 10.1038/nature21056.
[2] R. R. Selvaraju et al., "Grad-CAM: Visual explanations from deep networks via gradient-based localization," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), 2017, doi: 10.1109/ICCV.2017.74.
[3] P. Tschandl, C. Rosendahl, and H. Kittler, "The HAM10000 dataset, a large collection of multi-source dermatoscopic images of common pigmented skin lesions," Sci. Data, vol. 5, Art. no. 180161, 2018, doi: 10.1038/sdata.2018.161.
[4] A. Howard et al., "Searching for MobileNetV3," in Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV), 2019, pp. 1314–1324, doi: 10.1109/ICCV.2019.00140.
[5] Y. Liu et al., "A deep learning system for differential diagnosis of skin diseases," Nat. Med., 2020, doi: 10.1038/s41591-020-0842-3.
[6] K. Freeman et al., "Algorithm based smartphone apps to assess risk of skin cancer in adults: systematic review of diagnostic accuracy studies," BMJ, 2020, Art. no. m127, doi: 10.1136/bmj.m127.
[7] M. Groh et al., "Evaluating deep neural networks trained on clinical images in dermatology with the Fitzpatrick 17k dataset," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. Workshops (CVPRW), 2021, pp. 1820–1828, doi: 10.1109/CVPRW53098.2021.00201.
[8] World Health Organization, Ethics and Governance of Artificial Intelligence for Health: WHO Guidance. Geneva, Switzerland: WHO, 2021. [Online]. Available: https://www.who.int/publications/i/item/9789240029200
[9] R. Daneshjou et al., "Disparities in dermatology AI performance on a diverse, curated clinical image set," Sci. Adv., vol. 8, no. 32, Art. no. eabq6147, 2022, doi: 10.1126/sciadv.abq6147.
[10] M. Naqvi, S. Q. Gilani, T. Syed, O. Marques, and H.-C. Kim, "Skin cancer detection using deep learning—A review," Diagnostics, vol. 13, no. 11, Art. no. 1911, 2023, doi: 10.3390/diagnostics13111911.
[11] A. K. Nugroho, R. Wardoyo, M. E. Wibowo, and H. Soebono, "Image dermoscopy skin lesion classification using deep learning method: systematic literature review," Bull. Electr. Eng. Inform., vol. 13, no. 2, pp. 1042–1049, 2024, doi: 10.11591/eei.v13i2.6077.
[12] Law of the Republic of Kazakhstan No. 94-V, "On personal data and their protection," May 21, 2013 (as amended). [Online]. Available: https://adilet.zan.kz/rus/docs/Z1300000094. Accessed: Oct. 24, 2026.
[13] A. Ray, S. Sarkar, F. Schwenker, and R. Sarkar, "Decoding skin cancer classification: perspectives, insights, and advances through researchers' lens," Sci. Rep., vol. 14, Art. no. 30542, 2024, doi: 10.1038/s41598-024-81961-3.
[14] J.-W. Tjiu and C.-F. Lu, "Equity and generalizability of artificial intelligence for skin-lesion diagnosis using clinical, dermoscopic, and smartphone images: A systematic review and meta-analysis," Medicina, vol. 61, no. 12, Art. no. 2186, 2025, doi: 10.3390/medicina61122186.

### Reading and verification owner proposal

| Reading / verification assignment | Owner | Status |
|-----------------------------------|-------|--------|
| Verify full metadata and relevance for existing references [1]–[12] | TODO | TODO |
| Additional AI module sources | Arman | Done: [13], [14]; title, authors, year and DOI checked against the PMC and MDPI pages on 24 Oct 2026 |
| Additional mobile/mHealth trust sources | Amantai | TODO: confirm assignment and sources |
| Additional security/data-protection sources | Sultan | TODO: confirm assignment and sources |

## Open questions

- Supported class taxonomy and risk vocabulary: TODO.
- Suitability and terms of use for candidate datasets: TODO.
- Whether candidate models and datasets transfer to smartphone photographs: TODO.
- Explainability method and on-device versus server inference: TODO.
- Legal applicability of the cited personal-data law to skin photographs: TODO: check with supervisor.
