# 🎬 TMDB Movies Data Analysis — Exploratory Data Analysis

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-EDA-lightgrey?logo=pandas)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-informational?logo=plotly)
![Dataset](https://img.shields.io/badge/Records-1%2C375%2C553-success)
![Source](https://img.shields.io/badge/Source-Kaggle%20TMDB%202023-orange)

A comprehensive Exploratory Data Analysis (EDA) of the **TMDB Movies Dataset 2024** from Kaggle, covering **1,375,553 movies** spanning from 1865 to 2058. This project uncovers patterns in budget, revenue, genre popularity, production geography, and temporal trends across the global film industry.

---

## 📁 Repository Structure

```
├── TMDB Movies EDA.ipynb               # Main analysis notebook
├── TMDB EDA Report.pdf          # Full EDA report with all charts
└── README.md
```

---

## 📊 Dataset Overview

| Attribute | Value |
|---|---|
| Source | Kaggle – TMDB Movies Dataset 2024 |
| Raw Records | 1,376,742 |
| After Cleaning | 1,375,553 |
| Total Columns | 20 (+ 4 engineered) |
| Date Range | 1865 – 2058 |
| Primary Language | English (largest group) |

---

## 🧹 Data Cleaning & Preprocessing

- Removed **1,189 duplicate** records
- Replaced zeros with `NaN` in financial fields — budget (94.27%), revenue (98.19%), runtime (30.47%), vote_average (73.96%)
- Dropped `homepage` and `tagline` columns (>86% missing)
- Converted `release_date` to `datetime64`, `status` and `original_language` to `category`
- Applied **Min-Max normalization** to raw popularity scores (range: 0 → 2,994) scaled to [1, 10]

**Engineered Features:**

| Feature | Formula |
|---|---|
| `profit` | revenue – budget |
| `roi` | (profit / budget) × 100 |
| `is_profitable` | profit > 0 |
| `release_year` / `release_month` | Extracted from release_date |
| `primary_genre` | First genre from pipe-separated list |

---

## 🔍 Analysis Sections

### 1. Univariate Analysis
- Budget and revenue distributions are **heavily right-skewed**; log transformation reveals near-normal distributions
- Vote average clusters around **6.0–7.0** (mean: 6.15, median: 6.0) — TMDB users rate generously

### 2. Categorical Feature Analysis
- **English** dominates with 750,644 films; French, Spanish, German, and Japanese follow
- **Drama** is the most-produced genre (255,369 films); Documentary and Comedy follow
- **USA** leads production with 213,310 films; France, Japan, UK, Germany round out the top 5
- By volume: **BBC & Warner Bros.** lead; by average revenue: **Warner Bros.** tops at $3B average

### 3. Bivariate & Multivariate Analysis
- **Adventure** tops average popularity (4.3); Documentary and Music score lowest
- `budget_log ↔ revenue_log`: strong positive correlation (r = +0.92)
- `vote_average ↔ revenue`: near-zero correlation (r = +0.08) — **quality ≠ commercial success**
- Studio genre heatmap shows Warner Bros. has the most balanced portfolio; Toei Company leads in Animation

### 4. Statistical & Correlation Analysis

| Variable Pair | Pearson r | Interpretation |
|---|---|---|
| revenue ↔ profit | +0.98 | Near-perfect — profit derived from revenue |
| budget_log ↔ revenue_log | +0.92 | Very strong — budget drives revenue |
| budget ↔ revenue | +0.73 | Strong on raw scale |
| vote_count ↔ revenue | +0.56 | Moderate — popular films earn more |
| vote_average ↔ revenue | +0.08 | Very weak — quality ≠ box office |

### 5. Runtime Analysis
- Most films fall in the **80–120 minute** range; feature films cluster around **90–110 minutes**
- **Adventure** films: longest profitable runtime (avg 107 min, avg revenue $108M)
- **Horror** films: shortest (avg 72 min) yet strong ROI relative to low budgets
- **History** films: longest on average (122 min) but moderate revenue

### 6. Time Series Analysis
- Global production grew **113×** from 1900 (441 films) to 2023 (49,767 films)
- Three major growth phases: Post-WWI, Post-WWII Digital (1999–2008), Streaming (2010–2023)
- **COVID-19** caused only a 1.6% decline — streaming compensated for theater closures
- **2023** is the all-time peak year in the dataset

---

## 📈 Key Findings

| # | Finding |
|---|---|
| F1 | Budget–revenue log correlation r = +0.92 — strongest predictor of box office success |
| F2 | Only ~1.8% of films have reported revenue — financial analysis limited to theatrical subset |
| F3 | Films with budgets >$100M are profitable 83% of the time vs. 52% for micro-budget films |
| F4 | Vote average has near-zero correlation with budget and revenue |
| F5 | Adventure leads average revenue ($122M); Drama leads by volume (255K films) |
| F6 | Horror achieves strong ROI despite lowest runtime (72 min) and modest budgets |
| F7 | Production grew ~16× from the 1970s to 2023, driven by OTT platforms |
| F8 | US, UK, France, Germany, and India account for the majority of global film output |

---

## 🛠️ Tech Stack

- **Python** — Pandas, NumPy
- **Visualization** — Matplotlib, Seaborn, Plotly
- **Environment** — Jupyter Notebook

---

## 🚀 Getting Started

```bash
git clone https://github.com/your-username/tmdb-eda.git
cd tmdb-eda
pip install pandas numpy matplotlib seaborn plotly jupyter
jupyter notebook TMDB_EDA.ipynb
```

Download the dataset from [Kaggle – TMDB Movies Dataset 2024](https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies) and place it in the project root.

---

## 🔭 Future Work

- NLP topic modeling on movie overviews and keywords (LDA / BERTopic)
- Revenue/ROI prediction model using budget, genre, runtime, release_month
- Franchise/sequel premium analysis
- Time series forecasting of production volume by genre and country (ARIMA / Prophet)

---

## 👤 Author

**Kevin Savaliya**  
*Analysis performed on the TMDB Movies Dataset 2023 (Kaggle)*
