# CeryS Plant Disease Research

An experimental plant disease classification project developed for CeryS AI using EfficientNet-B3 and PyTorch.

The project investigates plant disease recognition across controlled and external image datasets, with particular attention to generalisation, domain shift, model limitations, and failure analysis.

## Current Model

**CeryS EfficientNet-B3 — Experimental v1**

- Architecture: EfficientNet-B3
- Output classes: 38
- Input resolution: 224 × 224
- Initial training dataset: PlantVillage
- Fine-tuning dataset: PlantDoc training split
- Framework: PyTorch

## Evaluation Results

| Evaluation | Accuracy | Macro F1 |
|---|---:|---:|
| PlantVillage test | 99.82% | 0.9973 |
| PlantDoc before fine-tuning | 25.37% | 0.2678 |
| PlantDoc after fine-tuning | 47.76% | 0.5023 |

PlantDoc external evaluation used 134 images across 16 explicitly mapped disease categories.

Fine-tuning used 1,400 PlantDoc training images, with an 80/20 training-validation split.

## Real-Image Testing

Additional tests using photographs sourced from the internet exposed failures not adequately represented by the initial benchmark.

The repository will document:
- Original test photographs and their reference labels.
- Top-three model predictions and confidence scores.
- Incorrect crop and disease predictions.
- Visual comparisons and failure analysis.

These tests are exploratory and are not part of the 134-image PlantDoc benchmark.

## Research Limitations

- Performance on PlantVillage does not establish field reliability.
- External evaluation currently covers only 16 mapped categories.
- The model retains its original 38-class output layer.
- Confidence scores are not calibrated diagnostic probabilities.
- Real-world photographs can differ significantly from training data.
- The model is not approved for independent agricultural diagnosis.

## Project Status

**Experimental research prototype — not production-ready.**

The existing CeryS AI production disease detection system remains separate from this model.

## Repository Roadmap

- [x] Train initial EfficientNet-B3 model.
- [x] Evaluate on PlantVillage.
- [x] Evaluate on PlantDoc.
- [x] Fine-tune using PlantDoc training data.
- [x] Evaluate fine-tuned model on PlantDoc test data.
- [x] Conduct initial external photograph tests.
- [ ] Build reusable inference module.
- [ ] Add confusion matrices and class-wise visualizations.
- [ ] Document individual prediction failures.
- [ ] Prepare reproducible evaluation scripts.
- [ ] Conduct broader field-image validation.

## Acknowledgements

This work uses the PlantVillage and PlantDoc datasets. Refer to their original publications and repositories for dataset attribution and licensing information.