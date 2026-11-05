# Limitations and Deployment Status

## Current status

CeryS EfficientNet-B3 Experimental v1 is a research prototype. It is not validated for independent diagnosis and must not replace the existing CeryS AI production disease-detection path.

## Evaluation limitations

1. **PlantVillage split independence:** the initial 70/15/15 split is image-level. It is not documented as a plant-, session- or source-independent split. Correlated images may appear across partitions.
2. **External test size:** the strict PlantDoc evaluation contains 134 images across 16 mapped categories. This is a small evaluation and does not represent all crops, disease stages or field conditions.
3. **Label mapping:** only explicitly mapped PlantDoc folders were included. The 16-folder mapping is a subset of the 38 model outputs.
4. **Taxonomy mismatch:** the classifier always returns one of 38 PlantVillage classes. It has no dedicated unknown / unsupported condition class.
5. **Fine-tuning scope:** PlantDoc fine-tuning used 1,400 images and an image-level stratified split. It does not establish robustness across farms, cameras, regions or seasons.
6. **Qualitative tests:** the two external image spot checks are illustrative only. One reference label was uncertain; the other was a documented grape black rot photograph on which the model failed.
7. **Confidence calibration:** softmax scores are not calibrated probabilities of correctness. A high score can accompany an incorrect prediction.
8. **Field validation:** no sufficiently large, prospectively collected and expert-labelled farm dataset has been evaluated.

## Deployment recommendation

Do not deploy this checkpoint for autonomous disease diagnosis. Keep it separate from the production detection pipeline. Any future field trial should include expert-confirmed labels, diverse farms and devices, explicit unknown-class handling, confidence calibration, per-crop metrics and a safe referral path when the model is uncertain.

## Reporting

Always report the PlantVillage and PlantDoc results separately. Do not present the 99.82% PlantVillage score as expected field accuracy. Keep qualitative external-image tests separate from the benchmark metrics.
