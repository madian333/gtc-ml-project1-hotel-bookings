# Hotel Bookings Analysis Project

## Overview
This repository contains the code and dataset for a machine learning project analyzing hotel booking data to predict cancellations (`is_canceled`). The project follows three phases: Exploratory Data Analysis (EDA), Data Cleaning, and Feature Engineering/Preprocessing, as part of the GTC ML Project 1.

## Repository Structure
- `hotel_bookings.csv`: The dataset containing 119,390 hotel booking records with 32 columns, including features like `lead_time`, `adr`, `is_canceled`, and more.
- `hotel_bookings_analysis.ipynb`: Jupyter notebook with the complete analysis, including:
  - **Phase 1**: EDA with summary statistics, missing value visualizations (missingno matrix, heatmap), and outlier detection (boxplots, IQR method).
  - **Phase 2**: Data cleaning, addressing missing values (`children`, `country`, `agent`, `company`), duplicates (31,994 removed), outliers (capped at domain-specific thresholds), and data type fixes (datetime for dates).
  - **Phase 3**: Feature engineering (e.g., `total_guests`, `total_nights`, `is_family`) and preprocessing (One-Hot Encoding for categorical variables, grouping infrequent `country` values, removing leakage columns, train/test split).
- `README.md`: This file, providing project details and instructions.

## Dataset
- **Source**: `hotel_bookings.csv` (hotel booking data).
- **Key Features**: `is_canceled` (target), `lead_time`, `adr`, `total_guests`, `total_nights`, `is_family`, and encoded categorical variables.
- **Size**: Originally 119,390 rows, reduced to 87,396 after duplicate removal.
- **Data Quality Issues**:
  - Missing values: Imputed `children` (mode=0), `country` ("Unknown"), `agent` (0), `company` (0).
  - Duplicates: Removed 31,994 duplicate rows.
  - Outliers: Capped in 11 numerical columns (e.g., `adr` at [0, 1000], `adults` at [0, 3]).
  - Data types: Converted `reservation_status_date` and created `arrival_date` as datetime.

## How to Run
1. **Requirements**:
   - Python 3.8+
   - Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `missingno`, `scikit-learn`
   - Install via: `pip install pandas numpy matplotlib seaborn missingno scikit-learn`
2. **Steps**:
   - Clone this repository: `git clone https://github.com/<your-username>/gtc-ml-project1-hotel-bookings.git`
   - Place `hotel_bookings.csv` in the same directory as `hotel_bookings_analysis.ipynb`.
   - Open the notebook in Jupyter: `jupyter notebook hotel_bookings_analysis.ipynb`
   - Run all cells to reproduce the analysis.
3. **Outputs**:
   - Visualizations (e.g., boxplots, missing value plots) are displayed inline.
   - Cleaned data and train/test splits are saved as CSV files (`cleaned_data_outliers_handled.csv`, `X_train.csv`, etc.).

## Notes
- The notebook assumes `hotel_bookings.csv` is in the working directory.
- The target variable is `is_canceled` (binary classification).
- Leakage columns (`reservation_status`, `reservation_status_date`) were dropped to ensure real-world applicability.
- Contact `<your-email>` for questions or issues.
