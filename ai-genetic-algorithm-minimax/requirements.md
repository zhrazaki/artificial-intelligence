# Environment & Dependencies — ai-genetic-algorithm-minimax

Python-kernel notebooks. No `requirements.txt` is committed; the environment
is documented here.

## Runtime

- **Python** ≥ 3.10 (developed on Google Colab)
- Jupyter Notebook / Google Colab

## R / Python Packages

| Package | Used by | Install |
|---|---|---|
| `numpy` | both notebooks | `pip install numpy` |
| `scipy` | WAV reading/writing (Genetic) | `pip install scipy` |
| `librosa` | audio feature handling (Genetic) | `pip install librosa` |
| `soundfile` | audio I/O (Genetic) | `pip install soundfile` |
| `matplotlib` | plots (both) | `pip install matplotlib` |
| `pygame` | checkers board rendering (MiniMax) | `pip install pygame` |

## Data / Assets

- Target melody `.wav` files are **not** redistributed (see README "How to
  Run"); place them in `Genetic/musics/` before running the Genetic notebook.
- One generated demo (`Genetic/my_ai_melody_ultimate.wav`) is committed.

## Reproducibility Notes

- Both notebooks are committed **executed**; all plots and logs are embedded.
- The GA is stochastic; re-running produces slightly different fitness curves
  unless seeds are fixed.
