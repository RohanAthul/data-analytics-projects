# Data Cleaning Pipeline - Electric Vehicle Dataset 2024 

This project focuses on the rigorous cleaning and preprocessing of a raw dataset containing specifications and pricing for Electric Vehicles (EVs) available in 2024. The primary objective is to transform raw, unstructured web-scraped data into a clean, structured format suitable for downstream exploratory data analysis (EDA) and predictive modeling.

### Dataset Details
- Source: EV Database (Data acquired in April 2024)

- Purpose: Strictly educational and data cleaning practice.

- Size: 351 rows, 16 columns (pre-cleaning).

- Input File: cars_data_RAW.csv

- Output File: cars_data_cleaned.xlsx (or .csv)
- Link to the dataset:  
    - https://www.kaggle.com/datasets/vanillatyy1/electric-vehicle-dataset/data

### Tech Stack & Dependencies
- Language: Python 3.x

- Core Libraries: pandas

- I/O & Utilities: pathlib, warnings, IPython.display

### Data Processing Pipeline
The pipeline systematically addresses inconsistencies, missing values, and formatting issues through the following stages:

- Feature Standardization: Column headers are renamed for programmatic consistency (e.g., price-range to KM_of_range, Tow_Hitch to Towbar_possible).

- Regex Data Extraction: Non-numeric characters (currency symbols like £, €, textual tags like 'N/A', and whitespace) are stripped from numerical columns using regular expressions.

- Currency Conversion: An Estimated_US_Value column is engineered by converting local prices to USD using specific exchange rates. A fallback logic (UK → Netherlands → Germany) ensures maximum data retention for missing price points.

- Boolean & Categorical Cleaning: The Towbar_possible feature is mapped to a binary format (1 for possible, 0 for missing/not possible).

- Grouped Statistical Imputation: Missing values in the Fastcharge column are imputed using the median of the respective Brand and Battery group. A cascading fallback fills remaining gaps using the Brand median, and finally, the global median.

- Cross-Country Price Imputation: Missing regional prices (Germany, Netherlands, UK) are estimated using historical price ratios. Germany is used as the base anchor to calculate ratios (e.g., UK/DE, NL/DE) to intelligently fill missing pricing data based on available regional equivalents.

- Data Type Optimization: Columns are cast to their appropriate types. Integer-based features are safely converted using the Pandas nullable integer type (Int64) to handle missing values without floating-point conversion errors.

### How to Run
- Ensure the raw data file is located at `./data/cars_data_RAW.csv.`

- Install necessary dependencies via pip: `pip install`

- Execute the script or run the Jupyter Notebook cells sequentially.

- The cleaned dataset will be exported to the `./data/` directory as `cars_data_cleaned.xlsx`.