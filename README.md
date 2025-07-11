

Installation for GAM
# --- Core numerical stack ---------------------------------------
numpy>=1.24
pandas>=2.2          # requires numpy ≥ 1.24
scipy>=1.11
statsmodels>=0.14    # 0.13+ needed for .fit_constrained()

# --- Visualisation ----------------------------------------------
matplotlib>=3.8
seaborn>=0.13        # pairs with matplotlib ≥ 3.7

# --- Generalised Additive Models --------------------------------
pygam>=0.9           # pre-built wheels for CPython 3.9-3.12

# --- Excel I/O ---------------------------------------------------
openpyxl>=3.1        # pandas ≥ 2.x no longer bundles older openpyxl
