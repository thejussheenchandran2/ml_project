# Exploring Dyslexia Patterns Using Machine Learning

**CSC1181 Machine Learning Project**

This project analyses data from an online gamified dyslexia screening test. It uses statistical tests to find patterns linked to dyslexia, builds classification models to predict dyslexia risk, and compares how well they perform. It also discusses how useful, reliable and fair machine learning is for dyslexia research.

## Dataset

- **Source:** Rello et al. (2020), *Predicting risk of dyslexia with an online gamified test*, PLoS ONE 15(12): e0241687. [doi:10.1371/journal.pone.0241687](https://doi.org/10.1371/journal.pone.0241687)
- **Download:** [Kaggle](https://www.kaggle.com/datasets/luzrello/dyslexia)
- **Size:** 3,644 participants aged 7–17; 392 (10.8%) have dyslexia
- **Columns (196):** gender, two language indicators, age, and six measures (clicks, hits, misses, score, accuracy, miss rate) for each of 32 reading and spelling tasks
- **Target:** `Dyslexia` (Yes / No)
- **Note:** the file is semicolon-separated, so read it with `pd.read_csv("Dyt-desktop.csv", sep=";")`

## Repository structure

```
├── Dyslexia_ML_Project_notebook.ipynb   main notebook (all outputs saved)
├── Dyt-desktop.csv                      dataset
├── figures/                             charts produced by the notebook
├── results/                             result tables (CSV)
└── README.md
```

## How to run

1. Install Python 3.10+ and the libraries:
   ```
   pip install pandas numpy scipy scikit-learn matplotlib seaborn jupyter
   ```
2. Open the notebook:
   ```
   jupyter notebook Dyslexia_ML_Project_notebook.ipynb
   ```
3. Choose **Run All**. It takes about one minute and recreates `figures/` and `results/`.

The saved outputs are visible directly on GitHub without running anything.

## Authors

| Name | Student ID |
|---|---|
| Joel John Thumpayil | A00099248 |
| Thejus Sheen Chandran | A00105644 |
| Augustine Ullas | A00099269 |
| Cerin Susan Prakash | A00097722 |
