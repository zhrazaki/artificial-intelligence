# Environment & Dependencies — ai-blood-cell-classification

Python-kernel notebook. No `requirements.txt` is committed; the environment is
documented here.

## Runtime

- **Python** ≥ 3.10 (developed on Google Colab)
- Jupyter Notebook / Google Colab

## Python Packages

| Package | Used for | Install |
|---|---|---|
| `torch` | model definition & training | `pip install torch --index-url https://download.pytorch.org/whl/cpu` (CPU) or `pip install torch` (CUDA build) |
| `torchvision` | `ImageFolder` dataset, transforms | `pip install torchvision` |
| `scikit-learn` | classification report, confusion matrix | `pip install scikit-learn` |
| `seaborn` | heatmaps | `pip install seaborn` |
| `matplotlib` | training curves, feature maps | `pip install matplotlib` |
| `pillow` | image loading | `pip install pillow` |

## Data

The full blood-cell dataset (~105 MB, 4,460+ images, 5 classes) is **not**
committed — see the README "Dataset" section for how to obtain and lay it out
(`archive/` next to the notebook). A few preview images live in
`dataset_samples/`.

## Reproducibility Notes

- The committed notebook contains the complete logs, plots, and metrics of
  the original training run.
- Training is stochastic; results vary slightly between runs unless seeds
  are fixed in every stochastic call.
- Full re-training (2 × 80 epochs) takes tens of minutes on CPU.
