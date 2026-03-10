# Publication-Ready Tables in R

A self-contained Quarto tutorial on producing publication-quality tables using
**gtsummary**, **flextable**, and **huxtable**, with real NHIS survey data.

## Contents

```
table-tutorial/
├── table_tutorial.qmd      # Main Quarto document
├── data/
│   └── nhis_sample.rds     # 20,000-row NHIS teaching sample
├── output/                 # Word exports go here (create if needed)
├── figures/                # Plots go here (create if needed)
└── README.md               # This file
```

## What This Tutorial Covers

| Section | Topics |
|---------|--------|
| Part 1 | `tbl_summary()` vs `tbl_svysummary()`, stratified Table 1 |
| Part 2 | `tbl_regression()`, removing reference rows, significance stars, footnote management, `show_header_names()` |
| Part 3 | `tbl_merge()` (side-by-side models), `tbl_stack()` (unweighted vs. weighted) |
| Part 4 | flextable export to Word via `as_flex_table()` + `save_as_docx()` |
| Part 5 | huxtable `huxreg()` for compact regression summaries |

## Requirements

Install required packages:

```r
install.packages(c(
  "tidyverse", "labelled", "survey",
  "gtsummary", "gt", "flextable", "huxtable",
  "sessioninfo"
))
```

## Rendering

### HTML (for GitHub Pages)
```bash
quarto render table_tutorial.qmd --to html
```

### PDF via typst
```bash
quarto render table_tutorial.qmd --to typst
```

### Both formats
```bash
quarto render table_tutorial.qmd
```

## Publishing to GitHub Pages

1. Initialize a Git repository in this folder and push to GitHub:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/table-tutorial.git
git push -u origin main
```

2. Publish with one command:

```bash
quarto publish gh-pages table_tutorial.qmd
```

Your tutorial will be live at `https://YOUR_USERNAME.github.io/table-tutorial/`.
On subsequent updates, just run `quarto publish gh-pages` again.

## Data Note

`data/nhis_sample.rds` is a 20,000-row random sample (seed = 2025) from the
NHIS 1997-2018 waves, linked to the National Death Index via the NHIS Linked
Mortality Files. The sample retains the survey design variables (`psu`,
`strata`, `wgt`) needed for weighted analysis.

For reproducibility, the full NHIS data can be downloaded from
[IPUMS NHIS](https://nhis.ipums.org/).

## Author

Muntasir Masum, PhD
Department of Epidemiology and Biostatistics
University at Albany, SUNY
