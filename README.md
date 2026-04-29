# E-wallet-company-Analysis

## Project Statement
This project analyzes payment and transaction data from an e-wallet company to understand product performance, transaction behavior, and operational insights. The goal is to support data-driven decision-making in payment systems and business performence monitoring.

## Objectives
- Perform Exploratory Data Analysis (EDA)
- Identify data quality issues
- Analyze product performance
- Segment transaction types
- Generate business insights

## Dataset Description 
|Dataset                  | Description |
|-----   |     ----|  
|payment_report.csv   |   Monthly payment volume by product 
|product.csv |  Product data 
|transactions.csv | Detailed transaction records

## Tools & Technologies
- Python (Pandas, NumPy)
- Jupyter Notebook

## Analysis

### Part I: Exploratory Data Analysis (EDA)

The first step of this project was to assess the quality and structure of the datasets before conducting further analysis. The EDA process focused on missing values, duplicates, incorrect data types, and abnormal numerical values.


#### 1_ payment_product dataset (merged payment_report dataset to product data set)

The `payment_product` dataset was created by merging `payment_report.csv` with `product.csv` using `product_id`.

##### Data Quality Checks

| Check | Findings | Action |
|---|---|---|
| Missing values | 22 missing values in 'category' <br> 22 missing values in 'team_own' | 'category' and 'team_own' are important for team performance and category contribution analysis, these missing values were removed |
| Duplicates | 5 duplicates found | Dropped duplicates |
| Incorrect data types | `report_month` was stored as object | Converted to datetime |
| Incorrect values | No negative payment volume found / X negative values found | No action / Investigated |

Overall, the `payment_product` dataset was suitable for analysis after basic cleaning. The main adjustment was converting date-related columns into the correct datetime format to support time-based analysis.

#### 2_ transactions dataset

The `transactions` dataset contains transaction-level records, including transaction type, merchant ID, sender, receiver, and transaction amount.

##### Data Quality Checks

| Check | Findings | Action |
|---|---|---|
| Missing values | X missing values found in column A | Reviewed impact before analysis |
| Duplicates | X duplicated `transaction_id` values found | Removed duplicates |
| Incorrect data types | Date column was stored as object | Converted to datetime |
| Incorrect values | X transactions had invalid or negative volume | Classified as invalid / removed from analysis |

The transactions dataset required additional checking because it contains row-level transaction records. Invalid transaction cases were identified based on the given transaction type rules and excluded from the final transaction-type performance summary.

#### Summary 



### Part II: Data Wrangling & Analysis

## Key Insights

## Project Structure

## How to Run 







