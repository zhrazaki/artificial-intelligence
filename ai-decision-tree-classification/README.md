# Decision Trees from Scratch — Four Classification Tasks

A from-scratch **decision tree classifier** (entropy / information gain) plus
scikit-learn model comparisons across four small classification tasks: spam
& message-loss detection, music-genre classification, trekking-safety
prediction, and student burnout.

## Academic Context

- **Course:** Artificial Intelligence
- **Institution:** School of Electrical and Computer Engineering, University of Tehran
- **Deliverable:** Computer Assignment 4 (CA4), single Python-kernel notebook
  (`CA4.ipynb`)

## Project Overview

The notebook (themed "DaneshChat AI Adventure") covers four tasks, each with
its own dataset in [`data/`](data/):

| Task | Dataset | Models / techniques |
|---|---|---|
| Spam & message-loss detection | `data/daneshchat_logs.csv` (6,000 messages) | Naive Bayes, Random Forest + `GridSearchCV`, and the scratch decision tree |
| Music-genre classification | `data/student_music_taste.csv` (1,000 students) | Scratch decision tree with one-hot encoding vs. sklearn `LogisticRegression`; imbalanced-metrics discussion |
| Trekking-safety prediction | `data/trekking_expedition.csv` (6,000 trips) | Decision trees with a feature-engineering experiment (`environmental_danger`) |
| Student burnout | `data/student_burnout.csv` (1,000 students) | Custom KNN (`k = 5`) |

## Methods

- **Decision tree from scratch:** entropy, information gain, recursive
  `build_tree`, majority-class leaves, `min_samples_split` /
  `min_samples_leaf` / `max_depth` control, and pandas-based prediction.
- Preprocessing: one-hot encoding of categorical features
  (`OneHotEncoder(handle_unknown="ignore")`), standardization
  (`StandardScaler`), stratified train/validation split.
- Model comparison with accuracy, precision, recall, F1 (macro/weighted),
  confusion matrices; explicit discussion of why accuracy misleads on
  imbalanced classes.
- Hyperparameter search with `GridSearchCV`; feature engineering
  (`environmental_danger` from slope/rain/cold) and before/after comparison.

## Technologies and Tools

- **Language:** Python (Jupyter Notebook / Google Colab)
- **Packages:** `numpy`, `pandas`, `scikit-learn`, `matplotlib`

## Repository Structure

```text
ai-decision-tree-classification/
├── README.md
├── CA4.ipynb          # fully executed notebook (all outputs embedded)
├── requirements.md
└── data/              # four CSV datasets (synthetic, anonymized)
    ├── daneshchat_logs.csv
    ├── student_burnout.csv
    ├── student_music_taste.csv
    └── trekking_expedition.csv
```

The notebook reads the CSVs with relative `data/...` paths, so it runs from
the repository root as-is.

## How to Run

```bash
pip install numpy pandas scikit-learn matplotlib
jupyter notebook CA4.ipynb
```

- Run top to bottom from the repository root (paths are relative).
- The committed notebook is fully executed; re-running is fast (~1 minute)
  and deterministic where seeds are set (`random_state=42`).

## Dependencies

See [`requirements.md`](requirements.md).

## Results and Key Findings

All numbers below are taken from the executed notebook's outputs.

- **Spam & message loss (daneshchat):** Naive Bayes reached **0.6817**
  accuracy (precision 0.7888), Random Forest with grid search **0.6900**, and
  the final comparison table reports **0.6883** for the best configuration.
- **Music-genre classification:** the scratch decision tree (with one-hot
  encoding, ~0.70 s training) reached **0.82** accuracy, slightly ahead of
  sklearn's `LogisticRegression` at **0.81**; on the imbalanced classes the
  notebook reports macro-F1 **0.746** vs. weighted-F1 **0.817**, illustrating
  why accuracy alone is misleading.
- **Trekking safety:** engineering the `environmental_danger` feature
  improved accuracy from **0.8533 → 0.8650** (+0.0117) and F1 from
  **0.8923 → 0.8982**.
- **Burnout:** the custom KNN (`k = 5`) reached **0.715** accuracy
  (macro-F1 0.714).

## Attribution

Assignment statement, task narratives, and starter/TODO templates are course
material; the completed implementations, model comparisons, and analysis are
the student's work for CA4.

## Compatibility Note

The original code passed `multi_class='multinomial'` to
`LogisticRegression`, a parameter removed in scikit-learn 1.7 (multinomial is
now the default behavior). The call was updated accordingly; results are
unchanged.
