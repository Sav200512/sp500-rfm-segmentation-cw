**S&P 500 stock segmentation using adapted RFM (6BUIS017W CRM & CM, CWK1)**

Individual coursework, University of Westminster / IIT. Student: S.R.G.Mangalaari ( W2151870, IIT 20232749).

**What this repository contains**
Task_1_2_and_3_cw_(20232749_W2151870).ipynb: the full Google Colab notebook (Task 1 data preparation, Task 2 clustering and sensitivity, Task 3 data mart and review). Saved with outputs.
data/raw/: data snapshots (daily Close, Adj Close, Volume for the S&P 500 constituents and ^GSPC, 1 Jan 2021 to 1 Jan 2025, end exclusive), the Wikipedia ticker list and run_log (retrieval time and package versions).
data/processed/: feature table (one row per included share), cluster assignments for the four baseline solutions, exclusion log, common share set, robustness and sensitivity tables.
figures/: figures used in the report.
requirements.txt: package versions.

**How to run**
Open the notebook in Google Colab (badge at the top of the notebook).
Run all cells in order. If Yahoo Finance is unreachable, skip the download cell and run the cached-data fallback cell, which loads data/raw/*.csv.gz.
Outputs are written to data/processed/ and figures/. The SQLite data mart is written to data/processed/sp500_mart.db.

**Key settings**
Observation date: 31 December 2024 (final common trading date). Seed: 42.
Weekly return and beta: Friday-ending weeks on Adj Close, 207 aligned weekly observations.
RFM: high-volume day = volume > 2 x mean of the previous 20 sessions; F and M use the latest 60 sessions.
Clustering: Ward (Euclidean) and K-means (k-means++, n_init=20), k = 2 to 8 compared; matrices standardised separately, log1p applied to M.
