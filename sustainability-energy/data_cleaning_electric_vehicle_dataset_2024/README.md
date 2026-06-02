# Data Cleaning Pipeline - Electric Vehicle Dataset 2024
This project focuses on the rigorous cleaning and preprocessing of a raw web-scraped dataset containing detailed specifications and pricing information for Electric Vehicles (EVs) from April 2024. The goal is to transform messy, inconsistent raw data into a clean, structured, analysis-ready dataset suitable for exploratory data analysis (EDA), visualization, and predictive modeling.
### Dataset Details

- Source: EV Database – April 2024
- Purpose: Strictly for educational and data-cleaning practice
- Raw Size: 351 rows × 16 columns
- Input File: `cars_data_RAW.csv`
- Output File: `cars_data_cleaned.xlsx`
- Kaggle Dataset: Electric Vehicle Dataset 2024

### Tech Stack & Dependencies

- Language: Python 3.x
- Core Library: pandas
- Utilities: pathlib, warnings, IPython.display

### Data Processing Pipeline
The pipeline systematically handles data quality issues through the following stages:

- Column Standardization: Renamed all columns for clarity and consistency (e.g., title → Brand, price-range → RangeValue, Tow_Hitch → Towbar_possible).
- Numeric Data Cleaning: Stripped all non-numeric characters (symbols, text, whitespace) from numerical columns using regex and converted them to proper numeric types.
- Brand Standardization: Converted all brand names to uppercase.
- Missing Value Handling:
  - `Towbar_possible`: Mapped to binary (1 = possible, 0 = not possible / missing).
  - `Towing_capacity_in_kg`: Filled NaNs with 0.
  - `Fastcharge`: Grouped median imputation (first by Brand + Battery, then by Brand, finally global median).
  - Regional prices (Germany, Netherlands, UK): Cross-country imputation using calculated market price ratios (UK/DE, NL/DE, UK/NL) with Germany as the primary anchor.

- Currency Standardization:
  - Converted UK prices (after incentives) from GBP to EUR using 2024 exchange rate (1 GBP = 1.17 EUR).
  - Created `Approx_price_in_USD` based on German price using 2024 exchange rate (1 EUR = 1.07 USD).

- Data Type Optimization: Converted all appropriate columns to nullable integer type (`Int64`) after rounding.
- Column Reordering: Rearranged columns into logical groups:
  - Identification
  - Battery & Performance
  - Utility & Interior
  - Financials (standardized to EUR and USD)

- Final Cleanup: Dropped the original GBP column and performed a final null check.

### Final Dataset

- Cleaned size: 351 rows
- Fully imputed and standardized
- Ready for analysis

### How to Run

1. Place the raw file at `./data/cars_data_RAW.csv`
2. Install dependencies: `pip install pandas openpyxl`
3. Run the Jupyter Notebook cell by cell.
4. The cleaned dataset will be automatically saved in the `./data/` folder as `cars_data_cleaned.xlsx`
