Exploring Dyslexia Patterns Using Machine Learning

CSC1181 Machine Learning Project

This project analyses data from an online gamified dyslexia screening test. It uses statistical tests to find patterns linked to dyslexia, builds classification models to predict dyslexia risk, and compares how well they perform. It also discusses how useful, reliable and fair machine learning is for dyslexia research.

Dataset
Source: Dytective online gamified test, desktop version: Rello et al. (2020), Predicting risk of dyslexia with an online gamified test, PLoS ONE 15(12): e0241687. doi:10.1371/journal.pone.0241687
Download: Kaggle, doi:10.34740/kaggle/dsv/1617514
Size: 3,644 participants aged 7–17; 392 (10.8%) have dyslexia
Columns (196): gender, two language indicators, age, and six measures (clicks, hits, misses, score, accuracy, miss rate) for each of 32 reading and spelling tasks
Target: Dyslexia (Yes / No)
Note: the file is semicolon-separated, so read it with pd.read_csv("Dyt-desktop.csv", sep=";")
Repository structure
├── Dyslexia_ML_Project_notebook.ipynb   main notebook (all outputs saved)
├── Dyt-desktop.csv                      dataset
├── figures/                             charts produced by the notebook
├── results/                             result tables (CSV)
└── README.md
How to run
Install Python 3.10+ and the libraries:
pip install pandas numpy scipy scikit-learn matplotlib seaborn jupyter
Open the notebook:
jupyter notebook Dyslexia_ML_Project_notebook.ipynb
Choose Run All. It takes about one minute and recreates figures/ and results/.

The saved outputs are visible directly on GitHub without running anything.

Method
Data-quality repair: 1,841 accuracy and 1,967 miss-rate values had lost their leading "0." (0.875 had become 875), affecting 1,371 participants. Because accuracy = hits ÷ clicks, both were recalculated exactly from the raw counts.
Exploratory analysis: summary statistics, class balance, distributions, outliers and correlations.
Feature engineering: 196 columns reduced to 10 features: gender, native language, other language, age, mean accuracy, accuracy variation, mean miss rate, total clicks, total hits, and tasks with zero hits.
Statistical tests: Mann–Whitney U and chi-square tests with effect sizes, Bonferroni-corrected.
Models: majority-class and random baselines, compared with logistic regression, random forest, gradient boosting and SVM. Class imbalance is handled with balanced class weights.
Validation: stratified 80/20 train/test split, with 5-fold stratified cross-validation and grid search on the training set.
Evaluation: recall, precision, F1, balanced accuracy, ROC AUC and PR AUC; bootstrap 95% confidence intervals; threshold trade-off.
Error and fairness analysis: performance by age group, gender and native language; permutation feature importance.
Key results (held-out test set, 729 participants)
Model	Recall	Precision	Balanced accuracy	ROC AUC
Majority baseline	0.00	0.00	0.50	0.50
Logistic regression (selected)	0.81	0.30	0.79	0.86
Random forest	0.77	0.30	0.78	0.85
Gradient boosting	0.74	0.30	0.77	0.87
SVM (RBF)	0.72	0.30	0.76	0.86
Patterns: participants with dyslexia clicked less and answered fewer items correctly, but their average accuracy was not significantly different. They appear to work more slowly rather than make more errors.
Performance: logistic regression detected 81% of dyslexic participants (95% CI 71–89%). This is close to the original study's result, using 10 features instead of 196.
Limitation: the model relies heavily on the native-language indicator. As a result, recall and false-alarm rates differ sharply between language groups.
Ethics

The data concern a health condition of children (a special category under GDPR Article 9). The dataset is anonymised and was published for research. A model like this should only indicate risk and recommend a professional assessment. It must never be used as a diagnosis.

Authors
Joel John Thumpayil - A00099248
Thejus Sheen Chandran - A00105644
Augustine Ullas - A00099269
Cerin Susan Prakash – A00097722
