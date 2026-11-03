# What Drives Car Price? — Automobile EDA

**Data Science Lifecycle (MSDS-1) — Advent 2026, Assignment One**
Uganda Christian University · Faculty of Engineering, Design and Technology

Exploratory data analysis and statistical testing on the `automobileEDA.csv`
dataset (201 cars, 29 attributes) to identify the variables that most strongly
influence car price.

## Contents

| Path | Description |
|---|---|
| `Assignment1_Ssekanabi.ipynb` | Main notebook — all five questions, code and written interpretation of every output |
| `automobileEDA.csv` | Dataset as provided |
| `Ssekanabi_Data.csv` | Cleaned dataset produced by Section 1 of the notebook |
| `data/raw/` | Untouched copy of the source data |
| `data/processed/` | Cleaned data written by the notebook |
| `figures/` | Charts exported as PNG |
| `requirements.txt` | Python dependencies |

## Notebook structure

1. **Data understanding and cleaning** — feature inventory, missing values,
   duplicates, outliers, redundant and pre-imputed columns; writes the cleaned file.
2. **Descriptive statistics and patterns** — summary statistics for continuous
   variables, frequency counts for categorical variables, distribution plots.
3. **Grouping** — average price by `drive-wheels`, `body-style` and other
   groupings, with a two-way pivot and heatmap.
4. **Effect of independent attributes on price** — continuous vs. price,
   categorical vs. price, and the interaction of two categorical variables.
5. **Key price drivers** — correlation, ANOVA F-test, mutual information and
   random-forest importance, consolidated into one ranking, plus a pricing
   recommendation for a car dealer.

## Running it

```bash
pip install -r requirements.txt
jupyter lab Assignment1_Ssekanabi.ipynb
```

Run all cells top to bottom. Section 1 writes `Ssekanabi_Data.csv`; later
sections read it, so the notebook is self-contained from the raw CSV.

## Dataset note

`automobileEDA.csv` is a pre-processed version of the UCI Automobile dataset, so
some cleaning was already applied before it reached me. `length` and `width` have
been scaled by dividing by the column maximum, `city-L/100km` is exactly
235 / `city-mpg`, `diesel` and `gas` are complementary flags for one variable, and
several values were mean-imputed upstream (`normalized-losses` is pinned at 122 on
41 rows, and two Renaults carry the mean horsepower and peak-rpm). Section 1 of the
notebook finds and documents each of these.

The cleaned file keeps all 201 rows. No outliers were removed: every value the IQR
rule flagged turned out to be a genuine luxury car, a diesel engine or a flat-four,
and the reasoning is set out in section 1.6.
