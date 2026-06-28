# Binder Showcase

A demonstration of Jupyter notebook features using the [Spambase dataset](https://archive.ics.uci.edu/ml/datasets/spambase) from the UCI Machine Learning Repository.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/<your-username>/binder_showcase/main)

## What's Demonstrated

The notebook `module_04_working.ipynb` covers:

- **Data loading & exploration** — reading the Spambase CSV with pandas, inspecting shape and head
- **Correlation analysis** — computing a full correlation matrix and rendering it as an interactive Plotly heatmap
- **Linear regression** — fitting a `scikit-learn` `LinearRegression` model, evaluating with R² and MSE
- **R integration via rpy2** — producing a `ggplot2` scatter plot and fitting an equivalent `lm()` model inside `%%R` cells, then pulling results back into Python
- **Interactive widgets** — `ipywidgets` dropdowns and checkboxes wired to a live scatter/regression plot via `interactive_output`
- **HTML embedding** — rendering arbitrary HTML inside a notebook cell
- **Markdown features** — bold/italic, ordered/unordered lists, code blocks, tables, and images
- **Debugging** — `pdb.set_trace()` / `%debug` usage inside a notebook
- **YAML config** — externalising parameters (`fit_intercept`, `chart_alpha`) into `config.yaml`

## Dataset

**Spambase** (Hopkins et al., Hewlett-Packard Labs, 1999)

| Property | Value |
|---|---|
| Instances | 4,601 |
| Attributes | 58 (57 continuous + 1 class label) |
| Spam | 1,813 (39.4%) |
| Non-spam | 2,788 (60.6%) |

Features include word frequency percentages, character frequency percentages, and capital-letter run-length statistics. The target column `spam_class` is `1` for spam and `0` for legitimate email.

## Project Structure

```
binder_showcase/
├── module_04_working.ipynb   # main notebook
├── config.yaml               # model and chart parameters
├── environment.yml           # conda environment (Python 3.10 + rpy2)
└── data/
    ├── spambase.data         # raw dataset (CSV, no header)
    ├── spambase.names        # feature names and descriptions
    └── spambase.DOCUMENTATION
```

## Running Locally

```bash
conda env create -f environment.yml
conda activate py310_new
jupyter notebook module_04_working.ipynb
```

> **Note:** `rpy2` and `ggplot2` are required for the R cells. The `environment.yml` installs `rpy2` via conda-forge; `ggplot2` is installed automatically inside the notebook on first run.

## Configuration

Edit `config.yaml` to adjust notebook behaviour without touching the notebook itself:

```yaml
fit_intercept: True   # whether the linear model includes an intercept
chart_alpha: 0.1      # scatter plot point transparency
```
