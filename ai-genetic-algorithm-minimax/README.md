# Genetic Algorithm & Minimax Game AI

Two classic AI search techniques implemented from scratch: a **genetic
algorithm** that evolves a melody to match a target song, and a **minimax
(with alpha–beta pruning)** AI that plays checkers.

## Academic Context

- **Course:** Artificial Intelligence
- **Institution:** School of Electrical and Computer Engineering, University of Tehran
- **Deliverable:** Computer Assignment 2 (CA2), two Python-kernel Jupyter
  notebooks: `Genetic/Genetic.ipynb` and `MiniMax/MiniMax.ipynb`

## Project Overview

| Part | Notebook | What it does |
|---|---|---|
| Genetic Algorithm | `Genetic/Genetic.ipynb` | extracts the target frequency sequence from a `.wav` song, evolves a chromosome of note frequencies toward it, plots the evolution, and synthesizes the result back to audio |
| Minimax | `MiniMax/MiniMax.ipynb` | implements minimax and alpha–beta pruning on top of a pre-built checkers engine and lets two AIs play full games |

## Contents

### Genetic/Genetic.ipynb — Melody Reconstruction using Evolution

- **Part 1 — Melody extraction:** `extract_frequencies_from_wav()` converts a
  target audio file into a sequence of note frequencies (mono conversion,
  windowed peak-frequency detection via FFT).
- **Part 2 — GA implementation:** `BestGeneticAlgorithm` class with
  configurable population size, generations, and mutation rate; fitness is
  based on the distance between a chromosome's frequencies and the target.
- **Part 3 — Visualization:** target vs. best chromosome on one figure,
  fitness/MAE evolution across generations.
- **Part 4 — The ultimate test:** `frequencies_to_melody()` (clean synth) and
  `frequencies_to_melody_ultimate()` (layered/echoed synth) write the evolved
  melody back to `.wav`.

### MiniMax/MiniMax.ipynb — Checkers with Minimax

- `minimax()` (plain) and `minimax_alpha_beta()` (with pruning) over the
  pre-built checkers game engine.
- Configurable evaluation functions to tune the AI's playing style.
- A full **AI-vs-AI game loop** (WHITE minimax AI vs RED opponent) reporting
  the winner and move statistics.

## Mathematical and Statistical Methods

- Genetic algorithm: selection, crossover, and mutation over a
  frequency-array chromosome; per-generation tracking of best fitness and
  mean-absolute-error (MAE) against the target sequence.
- Minimax search with recursive game-tree exploration; alpha–beta pruning for
  identical results with fewer evaluated nodes; heuristic board evaluation
  from the maximizing player's perspective.

## Technologies and Tools

- **Language:** Python (Jupyter Notebook / Google Colab)
- **Packages:** `numpy`, `scipy`, `librosa`, `soundfile`, `matplotlib`
  (Genetic) · `pygame`, `matplotlib` (MiniMax)

## Repository Structure

```text
ai-genetic-algorithm-minimax/
├── README.md
├── requirements.md
├── Genetic/
│   ├── Genetic.ipynb                  # GA melody reconstruction (executed)
│   └── my_ai_melody_ultimate.wav      # sample GA output (demo)
└── MiniMax/
    ├── MiniMax.ipynb                  # checkers minimax AI (executed)
    └── assets/crown.png
```

## How to Run

### Genetic notebook

The target song files are **not included** in this repository (audio size and
copyright). To reproduce:

1. Put one or more target melodies as `.wav` in `Genetic/musics/` named
   `<song>_target.wav` (the notebook references files such as
   `musics/mario_target.wav`).
2. Run `Genetic/Genetic.ipynb` top to bottom (Colab or local Jupyter).
3. The notebook synthesizes `my_ai_melody_clean.wav` and
   `my_ai_melody_ultimate.wav`; one generated demo
   (`my_ai_melody_ultimate.wav`) is committed as a sample output.

### MiniMax notebook

`MiniMax/MiniMax.ipynb` is self-contained (the checkers engine is defined in
the notebook). Run top to bottom; the final cells simulate full games.
`pygame` is needed for board rendering.

## Dependencies

See [`requirements.md`](requirements.md).

## Results and Key Findings

All findings below come from the executed notebooks.

- **GA convergence:** best fitness improved from **0.019 (Gen 0)** to
  **≈0.32 by generation 350**, with the frequency MAE dropping from
  **261 Hz to ≈26 Hz** during the run (training log in the notebook).
- **Synthesis:** the evolved chromosome was rendered to a playable
  `.wav` melody (demo committed).
- **Checkers AI:** the alpha–beta version plays complete games with the same
  decisions as plain minimax while evaluating substantially fewer nodes
  (pruning); evaluation-function variants change the AI's playing style.

## Attribution

Assignment statements and starter code fragments are part of the course
material; the GA implementation, alpha–beta search, evaluation heuristics,
and generated melodies are the student's work for CA2.
