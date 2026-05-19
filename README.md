# PCA-Based Breast Cancer Gene Expression Analysis

Principal Component Analysis (PCA) applied to breast cancer gene expression data to explore separation between ER-positive and ER-negative samples.

---

## Pipeline Overview

```
class.tsv  ──────────────────────────────────────────────►
columns.tsv.gz  ──►  Load & Extract GATA3/XBP1  ──►  PCA  ──►  Figures
filtered.tsv.gz  ────────────────────────────────────────►
```

---

## Requirements

- Python 3
- Google Colab (or any Jupyter environment)
- Libraries: `numpy`, `pandas`, `matplotlib` (all pre-installed in Colab)

---

## Data Files (upload to Colab before running)

| File | Description |
|------|-------------|
| `class.tsv` | ER status per sample (1 = ER+, 0 = ER−) |
| `columns.tsv.gz` | Gene ID and symbol metadata |
| `filtered.tsv.gz` | Gene expression matrix |

---

## How to Run

1. Open the notebook in **Google Colab**
2. Upload the 3 data files using the file panel on the left
3. Run all cells in order

---

## What the Notebook Does

1. **Loads** the expression matrix and ER class labels
2. **Extracts** expression values for two key ER+ marker genes — **GATA3** and **XBP1**
3. **Mean-centers** the features and builds the covariance matrix
4. **Computes eigenvalues and eigenvectors** manually using NumPy (no sklearn)
5. **Projects** samples onto PC1 and PC2
6. **Generates** three figures

---

## Results

| Output | Description |
|--------|-------------|
| `figure_1a.png` | Scatter plot of GATA3 vs XBP1 expression colored by ER status |
| `figure_1b.png` | Same scatter with PC1 and PC2 direction arrows overlaid |
| `figure_1c.png` | 1D projections onto PC1 for all samples, ER−, and ER+ separately |

- **PC1** explains ~78% of variance
- **PC2** explains ~22% of variance
- ER+ and ER− samples show clear separation along PC1

---

## PCA Workflow

1. **Mean-center** each feature
2. **Covariance matrix** from centered data
3. **Eigendecomposition** for principal directions
4. **Project** samples onto the leading components