# External Image Failure Analysis

These are qualitative spot checks using photographs sourced outside the PlantVillage and PlantDoc benchmark splits. They are not part of the 134-image PlantDoc test metric and must not be added to benchmark accuracy.

## Case 1 — Grape leaf photograph with uncertain reference label

**Reference label:** The image was initially selected as a grape black rot example, but visual inspection suggested grape erineum mite / grape leaf blister mite. The exact source caption was not independently confirmed. Treat this case as an uncertain-label example, not a scored grape black rot test.

Top predictions:

| Rank | Model prediction | Score |
|---|---|---:|
| 1 | Apple Cedar Rust | 39.55% |
| 2 | Grape Black Rot | 38.41% |
| 3 | Corn Common Rust | 15.67% |

Observation: the model did not confidently identify the expected grape condition. Because the reference label is uncertain and the likely condition may not exist in the 38-class taxonomy, this case demonstrates a taxonomy / out-of-distribution limitation rather than a definitive labelled error.

## Case 2 — Oklahoma State University grape black rot photograph

**Reference label:** Grape black rot  
**Reference image:** [Oklahoma State University Extension — black rot of grapes](https://extension.okstate.edu/e-pest-alerts/2024/images/a-2024-update-on-black-rot-of-grapes-in-oklahoma-sept-4-2024/fig-3c.jpg)

Top predictions:

| Rank | Model prediction | Score |
|---|---|---:|
| 1 | Apple Cedar Rust | 65.50% |
| 2 | Corn Gray Leaf Spot | 16.24% |
| 3 | Pepper Bacterial Spot | 11.30% |

Observation: the expected class, Grape Black Rot, did not appear in the top three. The model assigned its highest score to an apple disease class. This is a qualitative failure on an external photograph despite the class performing well in the PlantDoc test subset.

## Interpretation

The two spot checks are too few to estimate a generalisation rate. They do, however, show why dataset metrics alone are insufficient. Image composition, background, capture conditions, disease stage, label ambiguity and unsupported conditions may affect predictions.

Do not interpret softmax scores as calibrated probabilities of diagnostic correctness. Retain the original photographs and exact model checkpoint if these cases are used in future comparisons.
