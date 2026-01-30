# Anime Data Wrangling & Preprocessing (R)

## Overview
Data wrangling and preprocessing project focused on combining two anime datasets and preparing an analysis-ready dataset.
Key steps include data cleaning, type standardization, feature engineering, outlier detection (IQR), and transformations
(min–max scaling and log transforms).

## Data Sources (Kaggle)
- MyAnimeList Dataset (animes.csv): https://www.kaggle.com/datasets/marlesson/myanimelist-dataset-animes-profiles-reviews?select=animes.csv
- Top 10,000 Anime (Anime_Top10000.csv): https://www.kaggle.com/datasets/thomaskonstantin/top-10000-anime-movies-ovas-and-tvshows

## Key Work
- Merged datasets using an inner join (title ↔ Anime_Name)
- Cleaned fields (dates, numeric conversions) and removed irrelevant columns
- Reshaped messy columns (episodes/type and air years start/end)
- Feature engineering: Episode_Category, Genre_Count
- Data quality checks: missing values, inconsistencies, IQR outliers
- Transformations: Min–Max normalization and log transform (log1p) to reduce skew
- Exported cleaned dataset (optional): cleaned_transformed_dataset.csv

## How to Run
1. Download the two datasets from Kaggle and place them locally (do not commit raw data).
2. Open `src/data_wrangling_preprocessing.Rmd` in RStudio.
3. Install required packages (dplyr, tidyr, stringr, ggplot2, etc.).
4. Knit the report / run the script to reproduce outputs.

## Outputs
- Report: `report/Data_Wrangling_Report.pdf`
- (Optional) Clean dataset: `output/cleaned_transformed_dataset.csv`

