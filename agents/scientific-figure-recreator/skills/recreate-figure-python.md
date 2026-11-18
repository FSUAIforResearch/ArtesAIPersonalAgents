---
name: figure-recreator-python
description: Generates a self-contained Python script (matplotlib, seaborn, numpy, pandas) with seeded synthetic data to recreate an uploaded scientific figure locally. Use when the user attaches this skill, types /python, or asks to recreate a figure in Python.
---

# Recreate Figure in Python (`/python`)

## When to Apply This Skill
Use this skill whenever it is attached to the conversation, when the user types `/python`, or when the user asks to recreate an uploaded scientific figure using Python.

## Python Coding Requirements
Write a single, self-contained Python 3 script (`recreate_figure.py`) using only standard scientific libraries (`numpy`, `pandas`, `matplotlib`, and optionally `seaborn` or `scipy.stats`):

1. **Section 1: Seeded Synthetic Data Generator (`np.random.default_rng(42)`)**:
   - Build a clean `pandas.DataFrame` (`df`) whose group means, standard deviations/slopes, and sample sizes closely reproduce the visual patterns in the uploaded figure.
2. **Section 2: "Swap Your Own Data Here" Block**:
   - Include a commented-out `df = pd.read_csv("your_data.csv")` block listing the exact column names expected by the plotting code.
3. **Section 3: Publication Styling & Plotting**:
   - Use `plt.rcParams` for clean publication typography (sans-serif font, legible tick/label sizes).
   - Use `fig, axes = plt.subplots(...)` or `GridSpec` for multi-panel figures, adding bold panel letters (`A`, `B`) via `ax.set_title(..., loc="left", fontweight="bold")` or `ax.text(...)`.
   - Apply the exact extracted hex colors (`#RRGGBB`), error bars / shaded confidence bands (`ax.fill_between` or `ax.errorbar`), reference lines (`ax.axhline` / `ax.axvline`), and clean spines (`ax.spines[['top', 'right']].set_visible(False)`).
4. **Section 4: High-Resolution Local Export (Works Without a Screen)**:
   - Always save `recreated_figure.png` (`dpi=300, bbox_inches="tight"`) and vector `recreated_figure.pdf` (`bbox_inches="tight"`) **before** any display call, so the files exist even on servers, HPC clusters, or remote sessions with no display.
   - Do not rely on `plt.show()`. End the script with `if plt.get_backend().lower() != "agg": plt.show()` so it only opens a window when one is available.
   - Tell the user they can force headless mode with `MPLBACKEND=Agg python recreate_figure.py`.
5. Provide the terminal command to install requirements (`pip install numpy pandas "matplotlib>=3.4" seaborn`) and run the script.

## Keep the Script Lean (No "AI Slop")
Write the shortest script that still reproduces the figure faithfully and stays readable:
- Import only libraries the script actually uses; skip `seaborn`/`scipy` unless they save lines.
- Generate synthetic data with vectorized `numpy` calls, not loops or one-off helper functions.
- Set shared styling once in `plt.rcParams` instead of repeating it per axis; loop over panels/groups instead of copy-pasting plotting blocks.
- Use one short comment per section header; no comments that restate the code, no `print()` banners, no `if __name__ == "__main__":` wrapper.
- Aim for roughly 40–80 lines for a single-panel figure and under 120 for multi-panel figures.
- Outside the code block, keep the explanation to the visual deconstruction and the run command; do not re-explain the script line by line.
