# Google Play Store - Exploratory Data Analysis

> Uncovering patterns, trends, and insights hidden in 10,000+ apps across the Google Play Store ecosystem.

---

## Project Overview

This project performs end-to-end **data preprocessing** and **exploratory data analysis (EDA)** on the Google Play Store dataset. The goal is to understand app distribution, user behaviour, category trends, and rating patterns that drive app success on Android's largest marketplace.

---

## Project Structure

```
google-playstore-eda/
│
├── data/
│   ├── raw_data.csv               # Original dataset
│   └── cleaned_data.csv           # Cleaned & preprocessed dataset
├── visualization/
|   ├── category_proportion_pie_chart.jpg
|   ├── top_ten_apps.jpg
|   ├── univariate_analysis_categorical_features.jpg
|   ├── univariate_analysis_numerical_features.jpg
|   ├── most_popular_app_categories.jpg
|
├── |── preprocessing.ipynb        # Data cleaning & feature engineering
│   └── eda.ipynb                  # Exploratory data analysis & visualisations
│
└── README.md
```

---

## Data Preprocessing (`preprocessing.ipynb`)

The raw dataset required significant cleaning before analysis. Here's what was done:

### Issues Found & Fixed

| Feature | Issue | Fix Applied |
|---|---|---|
| `Reviews` | Non-numeric values present | Identified & dropped 1 corrupt row; cast to `int` |
| `Size` | Mixed units (`M`, `k`, `Varies with device`) | Standardised to numeric (KB); `Varies with device` → `NaN` |
| `Installs` | String format with `+` and `,` | Stripped special characters; cast to `int` |
| `Price` | String format with `$` | Stripped `$`; cast to `float` |
| `Last Updated` | Plain string | Parsed to `datetime`; extracted `Day`, `Month`, `Year` |

### Output
A clean, analysis-ready CSV — `googleplay_cleaned.csv` — with proper data types and structured date fields.

---

## Exploratory Data Analysis (`eda.ipynb`)

### Data Quality
- **Duplicate records** identified and removed (kept first occurrence per app name)

### Feature Types
- **Numerical features** — Rating, Reviews, Size, Installs, Price, Day, Month, Year
- **Categorical features** — App, Category, Type, Content Rating, Genres, etc.

---

### Key Findings

#### 1. Distribution of Numerical Features
- `Rating` and `Year` are **left-skewed** → most apps have high ratings and were updated recently
- `Reviews`, `Size`, `Installs`, and `Price` are **right-skewed** → a small number of apps dominate installs and reviews

#### 2. App Type & Content Rating
- The majority of apps on the Play Store are **free**
- **Everyone** is the dominant content rating, reflecting the family-friendly nature of most apps

#### 3. Most Popular App Categories
- **Family** dominates with ~19% of all apps, followed by **Games** (~11%)
- **Beauty**, **Comics**, **Art & Design**, and **Weather** categories are the least represented (<1% each)

#### 4. Most Installed Categories
- When ranked by **total installs**, the category landscape shifts — reflecting how a few mega-popular games and communication apps drive billions of downloads

#### 5. Five-Star Rated Apps
- **271 apps** have achieved a perfect 5.0 rating on the Play Store
- The top perfect-rated app is **'CT Brain Interpretation'** from the **Medical/Family** category

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Core language |
| `Pandas` | Data manipulation & cleaning |
| `NumPy` | Numerical operations |
| `Matplotlib` | Base visualisations |
| `Seaborn` | Statistical plots & styling |
| `Jupyter Notebook` | Interactive analysis environment |

---

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/google-playstore-eda.git
cd google-playstore-eda
```

### 2. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Run the Notebooks
```bash
jupyter notebook
```
Open `notebooks/preprocessing.ipynb` first, then `notebooks/eda.ipynb`.


## Dataset

The dataset used is the [Google Play Store Apps dataset](https://www.kaggle.com/datasets/lava18/google-play-store-apps) available on Kaggle, containing metadata on 10,000+ apps scraped from the Play Store.


## Author

Shahnawaz Khan
- LinkedIn: (www.linkedin.com/in/shahnawaz-khan-ds545)


## Source

This project is open-source.
