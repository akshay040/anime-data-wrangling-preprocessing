# Anime Data Wrangling & Preprocessing (R)

## Overview
This project demonstrates an end-to-end **data wrangling and preprocessing pipeline in R** using two Kaggle anime datasets. The goal is to **merge**, **clean**, **validate**, and **transform** the data into an **analysis-ready dataset** suitable for EDA, modeling, and reporting.

**Key steps**
- Data integration (join across sources)
- Data cleaning & type standardization
- Reshaping messy columns into structured fields
- Feature engineering for analytical usefulness
- Data validation (missingness + outlier checks via IQR)
- Scaling + log transforms to reduce skew and align numeric ranges

---

## Executive Summary (What I Did)
1. **Project Overview**  
   Focused on data wrangling and preprocessing of an anime dataset from two sources, aiming to merge datasets and improve analysis readiness.
2. **Data Import and Merging**  
   Merged two datasets on common columns: **`title`** and **`Anime_Name`** (inner join).
3. **Initial Data Cleaning**  
   Removed unnecessary columns such as **`img_url`** and **`link`**. Standardized dates and converted **`episodes`**, **`score`**, **`members`**, and **`popularity`** to numeric types. Converted **`genre`** to a factor.
4. **Data Structuring and Transformation**  
   Split **`Anime_Episodes`** into **`Type`** and episode count. Divided **`Anime_Air_Years`** into **`Airing_Start`** and **`Airing_End`**.
5. **Feature Engineering**  
   Created **`Episode_Category`** to classify anime by episode length, and **`Genre_Count`** to count number of genres.
6. **Data Validation**  
   Checked for missing values, inconsistencies, and outliers using the **IQR method**, supported by boxplots.
7. **Normalization and Log Transformation**  
   Normalized numeric columns into a **0–1 range** (min–max scaling) and applied **log transformation (log1p)** to handle skew (especially in members/popularity).

---

## Data Sources (Kaggle)
- **MyAnimeList Dataset** (`animes.csv`)  
  https://www.kaggle.com/datasets/marlesson/myanimelist-dataset-animes-profiles-reviews?select=animes.csv

- **Top 10,000 Anime** (`Anime_Top10000.csv`)  
  https://www.kaggle.com/datasets/thomaskonstantin/top-10000-anime-movies-ovas-and-tvshows

**Join key used**
- `title` (MyAnimeList dataset)  
- `Anime_Name` (Top 10,000 Anime dataset)  
Merged using **inner join** (keeps only matching anime titles).

## Repository Structure
anime-data-wrangling-preprocessing/
├─ README.md
├─ Report/
│ └─ Data Wrangling.pdf
├─ src/
│ └─ Data Wrangling.Rmd
├─ output/
  └─ cleaned_transformed_dataset.csv


---

## Cleaned Dataset (Output)

**File:** `output/cleaned_transformed_dataset.csv`

### What the cleaned dataset looks like
The cleaned dataset includes the following columns:

| Column | Description |
|---|---|
| `Title` | Anime title |
| `Genre` | Genres (categorical / list-like string) |
| `Type` | Format/type (TV/Movie/OVA/ONA/Special/Music) |
| `Airing_Start` | Airing start (date/year based on source) |
| `Airing_End` | Airing end (date/year based on source) |
| `Members` | Raw member count |
| `Normalized_Members` | Members scaled to 0–1 (min–max normalization) |
| `Log_Members` | Log-transformed members (log1p) |
| `Popularity` | Raw popularity metric/rank |
| `Normalized_Popularity` | Popularity scaled to 0–1 (min–max normalization) |
| `Log_Popularity` | Log-transformed popularity (log1p) |
| `Score` | Raw score |
| `Normalized_Score` | Score scaled to 0–1 (min–max normalization) |
| `Ranked` | Rank field from source |
| `Anime_Rating` | Rating field from source |
| `Episode_Category` | Engineered episode bucket (e.g., Short/Medium/Long) |
| `Genre_Count` | Engineered count of genres |

### Why these columns matter (analytics-ready)
This output supports:
- **EDA**: cleaner distributions + reduced skew via transformations  
- **Modeling**: normalized numeric features for fair comparisons  
- **Reporting**: structured, readable columns and engineered features

---

## How to Run (Reproduce Results)

### Run the R Markdown 
1. Download the Kaggle datasets and place them in:
   - `raw data/animes.csv`
   - `raw data/Anime_Top10000.csv`
2. Open: `src/Data Wrangling.Rmd` in RStudio
3. Install packages if required:
   ```r
   install.packages(c("dplyr","tidyr","stringr","ggplot2","magrittr","kableExtra"))
4. Click Knit (or run chunks)
5. The processed dataset should be generated/exported into:
   output/cleaned_transformed_dataset.csv


### Techniques Used

Data wrangling: join/merge, filtering, column selection, parsing

Type handling: numeric conversion, date parsing, categorical factor handling

Reshaping: splitting compound columns into meaningful fields

Feature engineering: Episode_Category, Genre_Count

Data validation: missingness checks, inconsistency checks, IQR outlier detection

Transformations: min–max normalization (0–1), log transformation (log1p)

Visualization: boxplots/histograms to validate distributions and outliers

### Tools & Skills Demonstrated

R: dplyr, tidyr, stringr, ggplot2, magrittr, kableExtra

Data Cleaning • Data Quality • Feature Engineering • Outlier Detection (IQR)

Normalization • Log Transformation • Analysis-ready dataset creation


Akshay Kumar
GitHub: https://github.com/akshay040
