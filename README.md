# 🤖 Artificial Intelligence Portfolio

A curated collection of four **independent, executed** projects from the
*Artificial Intelligence* course at the **University of Tehran** (School of
Electrical and Computer Engineering) — spanning deep learning, reinforcement
learning, evolutionary algorithms, adversarial search, and supervised
classification.

> Each folder below is a **self-contained project** with its own detailed
> `README.md`, notebook, and dependency documentation.

---

## 🗂️ Projects

| Folder | Focus | Key Tech |
|---|---|---|
| 🧬 [`ai-blood-cell-classification/`](ai-blood-cell-classification/) | **MLP vs CNN** on blood-cell microscopy images — error analysis, feature maps, spatial invariance, occlusion sensitivity | PyTorch |
| 🧠 [`ai-decision-tree-classification/`](ai-decision-tree-classification/) | Decision tree **from scratch** + sklearn comparison on four classification tasks | Python · scikit-learn |
| 🕹️ [`ai-qlearning-mountain-car/`](ai-qlearning-mountain-car/) | Tabular **Q-Learning** on MountainCar: ε strategies, discretization, 3D value function, reward shaping | gymnasium |
| 🎮 [`ai-genetic-algorithm-minimax/`](ai-genetic-algorithm-minimax/) | **Genetic algorithm** melody reconstruction + **minimax (α–β)** checkers AI | numpy · pygame |

---

## 🔍 At a Glance

- **ai-blood-cell-classification** — a fully connected network (88.0% test
  accuracy) versus a CNN (98.8%) on 4,460 blood-cell images across 5 classes,
  with softmax confidence analysis, feature-map visualizations, rotation/
  translation robustness tests, and occlusion-sensitivity heatmaps. *(Medical
  imaging / deep learning.)*
- **ai-decision-tree-classification** — entropy / information-gain tree built
  from first principles, compared with Naive Bayes, Random Forest
  (GridSearchCV), KNN, and Logistic Regression on spam detection, music-genre,
  trekking-safety, and burnout datasets; imbalanced-metrics discussion.
- **ai-qlearning-mountain-car** — 100,000-episode tabular Q-learning run with
  40×40 state discretization, exponential vs. fixed ε comparisons, value
  function surfacing, and reward shaping.
- **ai-genetic-algorithm-minimax** — a GA that evolves a note-frequency
  chromosome toward a target melody (fitness 0.019 → ≈0.32, MAE 261 Hz →
  ≈26 Hz) and synthesizes the result to audio, plus a minimax + alpha–beta
  checkers AI playing full games.

## 🧾 Conventions

- Notebooks are committed **executed** — all logs, plots, and metrics are
  embedded and readable without re-training.
- Each project has its own `requirements.md` with exact install commands and
  runtime notes.
- Datasets that are large or third-party (audio targets, blood-cell images)
  are **not committed**; each README explains how to obtain and lay them out,
  with small committed samples where useful.

## 🔗 Standalone Repositories

These projects are also published as independent repositories with full git
history:

[ai-blood-cell-classification](https://github.com/zhrazaki/ai-blood-cell-classification) ·
[ai-decision-tree-classification](https://github.com/zhrazaki/ai-decision-tree-classification) ·
[ai-qlearning-mountain-car](https://github.com/zhrazaki/ai-qlearning-mountain-car) ·
[ai-genetic-algorithm-minimax](https://github.com/zhrazaki/ai-genetic-algorithm-minimax)
