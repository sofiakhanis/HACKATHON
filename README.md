# TV Price Analysis Across Major Retailers

## Project Overview

This project analyzes TV product listings across four major online retailers — **Amazon, eBay, Target, and Walmart** — by cleaning the raw data, consolidating it into one structured format, generating Excel analytics with formulas and pivot table and applying machine learning techniques to uncover pricing trends and product groupings.

---

## Data Sources

Each dataset was collected through web scraping or download and saved as a `.csv` file:

- `amazon_tv_data.csv`
- `ebay_tv.csv`
- `target_tv_data_clean.csv`
- `walmart_tvs.csv`

All datasets share the same schema:
- `product_id`
- `product_name`
- `product_brand`
- `category`
- `price`
- `rating`
- `rating_count`
- `product_link`
- `smart_feature`
- `screen_size_inch`

---

## Step 1: Data Cleaning

For each dataset:
- Removed rows with missing or inconsistent pricing and screen size.
- Normalized brand names and category labels.
- Converted string columns (like price) into numeric types.
- Extracted numeric screen sizes and flagged "Smart TV" functionality as Yes/No.

---

## Step 2: Excel Automation

We used Python (`xlsxwriter`) to generate an Excel report with the following:

### `All_TVs` Sheet
- All cleaned data from all four stores.
- Automatically formatted headers and columns.
- Added a new column `store` to identify the origin (Amazon, eBay, Target, Walmart).
- Created a `size_segment` column to bucket TVs by screen size: **Small (<30")**, **Medium (30-49")**, **Large (50-69")**, **XL (70+")**.
- Two new computed columns:
  - `Smart_TV` = Yes/No based on `smart_feature`
  - `size_segment` = size category from screen size

### `Summary` Sheet
- Aggregated insights using Excel formulas:
  - Average price per store
  - Average screen size per store
  - Count of Smart TVs per store
  - Total TV listings per store

### `Pivot` Table
- A pivot table created in Excel (manually) to compare price averages across brands covering different sizes.

---

## Step 3: Machine Learning Analysis

Using `scikit-learn`, we applied:

### K-Means Clustering
- Grouped TVs based on **price**, **screen size**, and **smart feature**.
- Helped identify product segments (e.g., budget vs. premium TVs).

### Linear Regression
- Modeled price trends over an artificial `time_index` (using sorted `product_id`).
- Allowed us to predict future price trends assuming product ID order reflects listing time.

### Logistic Classification (Bonus)
- Predicted whether a TV is Smart or not using features like price, size, and rating.

---

## Output

- `amazon_tv_data.csv`: CSV file with clean Amazon database
- `ebay_tv.csv`: CSV file with clean eBay database
- `target_tv_data_clean.csv`: CSV file with clean Target database
- `walmart_tvs.csv`: CSV file with clean Walmart database
- `TV_Comparison_total.xlsx`: Main Excel file with formulas and visual insights.
- `MachineLearningProject.ipynb`: Scripts and model outputs for clustering and regression.

---

## Team Members

- **Sofia Khanis**
- **Joel Abadi**

---

## Dependencies

- `pandas`
- `numpy`
- `xlsxwriter`
- `scikit-learn`
- `matplotlib`
- `seaborn`

---

## How to Run

```bash
# Install dependencies
pip install pandas numpy xlsxwriter scikit-learn matplotlib seaborn

# Run the Python script
In each folder for each website run according .ipynb file to see the code. 
In folder Excel_Analysis run ExcelTvAnalysis.ipynb to see the code or open TV_Comparison_total.xlsx to see the final worksheet. 
In folder Machine_Learning run MachineLearningProject.ipynb to see the code and plots. 
