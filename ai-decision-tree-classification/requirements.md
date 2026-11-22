# Environment & Dependencies — ai-decision-tree-classification

Python-kernel notebook. No `requirements.txt` is committed; the environment
is documented here.

## Runtime

- **Python** ≥ 3.10 (developed on Google Colab; verified locally with
  Python 3.14)
- Jupyter Notebook / Google Colab

## Python Packages

| Package | Used for | Install |
|---|---|---|
| `numpy` | tree math, arrays | `pip install numpy` |
| `pandas` | DataFrames, `.iterrows()` prediction | `pip install pandas` |
| `scikit-learn` | NB/RF/KNN/LogReg, preprocessing, metrics, GridSearchCV | `pip install scikit-learn` |
| `matplotlib` | plots | `pip install matplotlib` |

**Version note:** tested with scikit-learn ≥ 1.7 (the notebook no longer
passes the removed `multi_class` argument; see the README compatibility
note). `OneHotEncoder(..., sparse_output=False)` requires scikit-learn ≥ 1.2.

## Data

The four CSV files in `data/` are small (≈345 KB total), synthetic course
datasets with anonymized numeric/categorical columns and label columns
(`is_spam`, `is_lost`, `music_genre`, `is_safe`, `mental_state`). They are
committed with the repository, so no download step is needed.

## Reproducibility Notes

- The committed notebook is **fully executed**; all metrics, tables, and
  plots are embedded.
- Splits use `random_state=42` and `stratify`, so re-running is essentially
  deterministic; the full run takes about a minute on a typical machine.
