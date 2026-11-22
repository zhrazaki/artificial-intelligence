# Blood Cell Classification — MLP vs CNN

Comparison of a **fully connected neural network (MLP)** and a **convolutional
neural network (CNN)** on blood-cell microscopy images, built with PyTorch —
covering training, error analysis, feature-map visualization, spatial-invariance
testing, and occlusion-sensitivity heatmaps.

## Academic Context

- **Course:** Artificial Intelligence
- **Institution:** School of Electrical and Computer Engineering, University of Tehran
- **Deliverable:** AI course assignment, implemented as a single Python-kernel
  notebook (`blood_cell_classification.ipynb`)

## Project Overview

The notebook trains both architectures from scratch on a 5-class blood-cell
image dataset (4,460 images, 64×64) and contrasts their behavior:

| Part | Topic |
|---|---|
| Setup | Normalization rationale, dataset loading (`ImageFolder`), train/test split, augmentation transforms |
| Part 1 | **MLP** — fully connected architecture with dropout regularization, trained for 80 epochs |
| Part 2 | **CNN** — convolutional architecture (kernel-size discussion), trained for 80 epochs |
| Part 3 | **Error analysis** — confusion matrix, classification report, high-confidence errors, softmax output inspection |
| Part 4 | **Feature-map visualization** — what the convolutional filters actually learn |
| Part 5 | **Spatial invariance test** — rotation & translation robustness: MLP vs. CNN |
| Part 6 | **Occlusion sensitivity** — heatmap of the image regions driving each prediction |

## Methods

- Data pipeline with `torchvision.transforms`: resized to 64×64, normalized,
  augmentation on the training split (`RandomRotation`, `RandomHorizontalFlip`).
- **MLP:** flattened 64×64×3 input through fully connected layers with
  dropout — learns global pixel patterns but ignores spatial structure.
- **CNN:** stacked convolution + pooling layers with small kernels
  (weight sharing and locality), followed by a classification head.
- Evaluation: per-class precision/recall/F1, confusion matrices, softmax
  confidence analysis, occlusion-sensitivity maps.

## Technologies and Tools

- **Language:** Python (Jupyter Notebook / Google Colab)
- **Framework:** PyTorch + torchvision
- **Libraries:** `scikit-learn` (metrics), `seaborn`, `matplotlib`, `Pillow`

## Repository Structure

```text
ai-blood-cell-classification/
├── README.md
├── blood_cell_classification.ipynb  # fully executed notebook (training logs, plots, metrics)
├── requirements.md
└── dataset_samples/      # 3 sample images per class (preview only)
```

## Dataset

The full dataset (**"Blood Cell Images for Cancer Detection"** — 5,000 images,
5 classes: `basophil`, `erythroblast`, `monocyte`, `myeloblast`,
`seg_neutrophil`) is **not committed** to this repository due to its size
(~105 MB) and third-party licensing.

To reproduce:

1. Obtain the dataset (provided through the course; also searchable on Kaggle
   as *Blood Cell Images for Cancer Detection*).
2. Place it next to the notebook as:
   ```text
   archive/
   ├── basophil/          # 1,000 images
   ├── erythroblast/      # 1,000 images
   ├── monocyte/          # 1,000 images
   ├── myeloblast/        # 1,000 images
   └── seg_neutrophil/    # 460 images
   ```
3. The notebook expects the root-relative path `./archive` (`DATASET_PATH` in
   the setup cell — adjust it there if you place the data elsewhere).

`dataset_samples/` contains a few preview images per class so the data layout
is visible without downloading the full dataset.

## How to Run

```bash
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
pip install scikit-learn seaborn matplotlib pillow
jupyter notebook blood_cell_classification.ipynb
```

- Run top to bottom from the directory containing `archive/`.
- Training (80 epochs MLP + 80 epochs CNN) is the long part: expect **tens of
  minutes on CPU**, faster on GPU.
- The committed notebook contains the complete logs, plots, and metrics of the
  original run, so all results can be read without re-training.

## Dependencies

See [`requirements.md`](requirements.md).

## Results and Key Findings

All numbers below come from the executed notebook's outputs.

- **MLP: 88.00% test accuracy** after 80 epochs (validation accuracy
  fluctuated around 70–79%; classification report mean accuracy 0.88 on
  1,000 test images).
- **CNN: 98.80% test accuracy** after 80 epochs, with training accuracy
  approaching 100% (classification report 0.99).
- **CNN ≫ MLP (+10.8 points)** — the convolutional architecture captures
  local morphological features of the cells that a fully connected network
  cannot exploit.
- **Spatial invariance:** the CNN degrades gracefully under rotation and
  translation while the MLP's accuracy drops sharply (plots in Part 5).
- **Occlusion sensitivity:** heatmaps concentrate on the nucleus region of
  the cells, showing the models base their decisions on biologically
  meaningful structures (Part 6).

## Attribution

Assignment statement, part structure, and starter template are course
material; the model implementations, training, and analysis are the
student's work for this assignment.
