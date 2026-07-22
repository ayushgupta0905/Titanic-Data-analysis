# Titanic Survival Analysis — EDA & Visualization

Exploratory data analysis, data cleaning, and visualization of the Titanic passenger dataset to understand the factors associated with survival.

## 📁 Repository Structure

```
├── Titanic.csv           # Raw dataset
├── Cleaning.ipynb         # Data exploration & cleaning notebook
├── Visulaization.ipynb    # EDA visualizations & insights notebook
└── README.md
```

## 📊 Dataset

The [Titanic dataset](https://www.kaggle.com/c/titanic/data) contains information on 891 passengers, including demographics, ticket class, fare, and survival outcome.

| Column | Description |
|---|---|
| PassengerId | Unique passenger identifier |
| Survived | Survival (0 = No, 1 = Yes) |
| Pclass | Passenger class (1 = Upper, 2 = Middle, 3 = Lower) |
| Name | Passenger name |
| Sex | Gender |
| Age | Age in years |
| SibSp | # of siblings/spouses aboard |
| Parch | # of parents/children aboard |
| Ticket | Ticket number |
| Fare | Passenger fare |
| Cabin | Cabin number |
| Embarked | Port of embarkation (C, Q, S) |

## 🧹 Data Cleaning (`Cleaning.ipynb`)

- Checked dataset shape, structure, and data types (`df.info()`, `df.describe()`)
- Checked for duplicate rows — none found
- **Age** (177 missing values): filled using the median age grouped by `Sex`, rather than a flat median, for a more accurate estimate
- **Embarked** (2 missing values): filled using the most frequent port (mode)
- **Cabin** (687 missing values, ~77%): left unfilled — too sparse to impute reliably; flagged for feature engineering (e.g. `HasCabin`) rather than direct imputation
- Verified all cleaning steps with `isnull().sum()` checks after each step

## 📈 Exploratory Data Analysis & Visualization (`Visulaization.ipynb`)

Visualizations built with `matplotlib` and `seaborn`, covering:

- **Gender distribution** — bar chart of passenger counts by sex
- **Passenger class distribution** — pie chart of 1st/2nd/3rd class passengers
- **Overall survival count** — bar chart of survived vs. died
- **Survival rate by gender** — bar chart comparing male vs. female survival rates
- **Survival rate by passenger class** — bar chart across 1st, 2nd, 3rd class
- **Passengers by port of embarkation** — bar chart of boarding locations
- **Age vs. Fare scatter plot** — colored by survival outcome
- **Age distribution** — histogram of passenger ages

### 🔑 Key Insights

- **Gender was the strongest predictor of survival**: ~74% of women survived vs. ~19% of men, reflecting a "women and children first" evacuation priority.
- **Passenger class strongly influenced survival**: survival rates were ~63% (1st class), ~47% (2nd class), and ~24% (3rd class) — likely tied to cabin location and lifeboat access.
- Most passengers (**~646, ~72%**) boarded at **Southampton (S)**, with fewer from Cherbourg (C) and Queenstown (Q).
- **Fare correlated with survival** — survivors paid noticeably higher average fares than non-survivors, consistent with the class effect above.
- **Age distribution** was concentrated between 20–35 years, with a median age of ~29; very young children showed slightly better survival odds.

## 🛠️ Tech Stack

- Python
- pandas, numpy
- matplotlib, seaborn
- Jupyter Notebook

## 🚀 How to Run

```bash
git clone <your-repo-url>
cd <repo-folder>
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook
```

Run `Cleaning.ipynb` first to generate the cleaned dataset, then open `Visulaization.ipynb` for the EDA and visualizations.

## 📌 Status

- [x] Data exploration & cleaning
- [x] Exploratory data analysis & visualizations
- [ ] Feature engineering for ML readiness
- [ ] Model training *(not required for this submission — see project guidelines)*
