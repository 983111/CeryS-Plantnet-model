# Methodology

## Model

- Architecture: torchvision EfficientNet-B3
- Initialisation: ImageNet-pretrained weights
- Input: RGB images resized to 224 × 224
- Output layer: 38 PlantVillage classes
- Framework: PyTorch

## PlantVillage training

The initial model was trained on 54,305 PlantVillage images across 38 classes. The notebook uses an image-level random split with a fixed seed:

- 70% training: 38,013 images
- 15% validation: 8,145 images
- 15% test: 8,147 images

Training configuration recorded in the experiment:

- Batch size: 32
- Optimiser: AdamW
- Initial learning rate: 1e-4
- Weight decay: 1e-4
- Loss: cross-entropy
- Scheduler: ReduceLROnPlateau
- Epochs: 10
- Training augmentation: horizontal flip, rotation and colour jitter
- Normalisation: ImageNet mean and standard deviation

The image-level split does not establish independence by plant, capture session or source. Near-duplicate or correlated images across splits may inflate the apparent test performance. This should be treated as a limitation of the benchmark.

## PlantDoc external evaluation

The original PlantVillage model was evaluated on 134 PlantDoc test images from 16 explicitly mapped disease folders. Generic folders and ambiguous labels were excluded from this strict evaluation.

The strict mapping covered apple scab, apple cedar rust, corn gray leaf spot, corn common rust, grape black rot, pepper bacterial spot, potato early and late blight, squash powdery mildew, and selected tomato diseases.

The original 38-class output layer was retained. Therefore, the model could predict classes outside the 16 mapped target categories.

## PlantDoc fine-tuning

The fine-tuning run used 1,400 images from the PlantDoc training directory across the same 16 mapped categories.

- Split: stratified 80% training / 20% validation
- Training images: 1,120
- Validation images: 280
- Batch size: 16
- Epochs: 8
- Early feature blocks: frozen
- Final feature block(s) and classifier: trainable
- Optimiser: AdamW
- Feature learning rate: 1e-5
- Classifier learning rate: 1e-4
- Weighted cross-entropy loss
- Best checkpoint selected by validation macro F1

The PlantDoc test directory was not used for gradient updates or checkpoint selection. The same 134-image strict test subset was used for the before/after comparison.

## Metrics

Accuracy is the fraction of correct predictions. Macro F1 is the unweighted mean of per-class F1 scores across the 16 evaluated target classes. Predictions into the other 22 model classes count as incorrect for their true target class.

## Reproducibility notes

The notebook is the primary experiment record. Re-running the notebook may require downloading the datasets and installing compatible versions of PyTorch, torchvision, scikit-learn, Pillow, NumPy and Matplotlib. Random seeds, library versions and dataset revisions should be recorded when reproducing the experiment.
