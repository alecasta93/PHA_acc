# VFA Compositional & Multivariate Analysis Toolkit

A collection of three standalone Python ≥ 3.9 workflows used in the paper **“Impact of VFA Composition on PHBV Production and Properties in Mixed Microbial Cultures”** (Castagnoli et al., 2025).
Each script addresses a different statistical question:


**`vfa_workflow.py`**  --> Generalised Additive Models (GAM) on centred-log-ratio (CLR) variables, optimisation & 3-D response surfaces
**`network_diagram.py`**  --> Cluster-aware network diagram of a correlation matrix (SVG + PDF)
**`multivariate_workflow.py`** --> Five-number summaries, Shapiro–Wilk, Pearson & partial correlations, PCA biplot, custom box-plots

> **Python ≥ 3.9 is mandatory** because `networkx 3.x` and `statsmodels 0.14` have dropped support for older interpreters.

---

## 1 · Installation

### 1.1 — single environment (all workflows)

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt          # master list, covers everything
```

### 1.2 — lightweight per-workflow setup

```bash
pip install -r requirements-gam.txt      # vfa_workflow.py only
pip install -r requirements-network.txt  # network_diagram.py only
pip install -r requirements-stat.txt     # multivariate_workflow.py only
```

A ready-made **`environment.yml`** for Conda/Mamba is provided in `/env/`.
Universal2 wheels make Apple-silicon installs painless (no compilation needed).

---

## 2 · Requirements (minimum tested versions)

### 2.1 — shared scientific stack

```
numpy>=1.24   pandas>=2.2   matplotlib>=3.8   openpyxl>=3.1   seaborn>=0.13
```

### 2.2 — extras by workflow


**Workflow-specific extra dependencies**

* **GAM workflow (`vfa_workflow.py`)**
  `scipy>=1.11`, `statsmodels>=0.14`, `pygam>=0.9`
  *Note – the helper `statsmodels.fit_constrained` exists only from version 0.13 onward.*

* **Network diagram (`network_diagram.py`)**
  `networkx>=3.2`
  *Requires Matplotlib ≥ 3.5 for the edge-routing options used in the script.*

* **Multivariate workflow (`multivariate_workflow.py`)**
  `scikit-learn>=1.4`, `statsmodels>=0.14`, `scipy>=1.11`
  *Wheels for scikit-learn ≥ 1.4 ship with OpenBLAS ≥ 0.3.23, so no external BLAS installation is needed.*

---

## 3 · Quick start

```bash
# ── GAM compositional workflow ────────────────────────────────
python vfa_workflow.py data/vfa_measurements.xlsx --out results_gam

# ── Correlation network diagram ───────────────────────────────
python network_diagram.py corr/correlation_matrix.xlsx \
       --alpha corr/alpha_flags.xlsx --out figs_network

# ── Multivariate statistical workflow ─────────────────────────
python multivariate_workflow.py data/experimental_data.xlsx --out results_stat
```

Each script builds an output folder (PDF, SVG, PNG, LaTeX/CSV/XLSX tables) and prints a concise log to console.

---

## 4 · Reproducibility

* Global random seed **`SEED = 42`** set with both `random` and NumPy.
* Figures exported as **PDF** (vector, publication-ready) and **PNG** (quick preview).
* GitHub Actions run smoke-tests on a toy dataset to ensure future commits remain functional.

---

## 5 · Citing this repository

```bibtex
@software{Castagnoli_2025_VFA,
  author    = {Castagnoli, Alessio},
  title     = {Impact of VFA Composition on PHBV Production and Properties in Mixed Microbial Cultures},
  year      = {2025},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.1234567},
  url       = {https://doi.org/10.5281/zenodo.1234567}
}
```

The DOI badge in the repository header always resolves to the exact version cited.

---

## 6 · License and governance

Released under the **MIT License** (see `LICENSE`).
Pull-requests are welcome—open an issue first for large changes.

---

## 7 · Contact

*Dr Alessio Castagnoli* — [alessio.castagnoli@ispra.it](mailto:alessio.castagnoli@ispra.it)
CN-COS, Livorno section, ISPRA (Rome, Italy)

For questions or feature requests, please use the GitHub **Issues** tab whenever possible.
