# Ewallet-transaction-analytics
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
| Incorrect values | No negative payment volume found | No action  |

Overall, the `payment_product` dataset was suitable for analysis after basic cleaning. The main adjustment was converting date-related columns into the correct datetime format to support time-based analysis.

#### 2_ transactions dataset

The `transactions` dataset contains transaction-level records, including transaction type, merchant ID, sender, receiver, and transaction amount.

##### Data Quality Checks
 Check | Findings | Action |
|---|---|---|
| Missing values |  49059 missing values found in column 'sender_id' <br> 164 795 missing values found in 'receiver_id' column  <br> 1 317 907 missing values found in column 'extra_info' | Removed missing values in both 'sende
|r_id' and 'receiver_id' |
| Duplicates | 28 duplicated `transaction_id` values found | Removed duplicates |
| Incorrect data types | 'sender_id' and 'receiver_id' column was stored as float64 | Converted to int64 |
| Incorrect values | No transactions had invalid or negative volume |  No action |

The transactions dataset required additional checking because it contains row-level transaction records. Invalid transaction cases were identified based on the given transaction type rules and excluded from the final transaction-type performance summary.


# Part II: Data Wrangling & Analysis

This section focuses on cleaning, transforming, validating, and analyzing transactional datasets using Python and Pandas.

Datasets used:
- `payment_report.csv`
- `product.csv`
- `transactions.csv`

---

## The Analysis Includes

- Aggregation analysis
- Business rule validation
- Contribution analysis
- Transaction classification
- KPI summarization

---

## Libraries Used

- `pandas`
- `numpy`

---

# Key Insights

## Top 3 Products by Volume

The top-performing products based on total transaction volume were:

| Rank | product_id | Total Volume |
|---|---|---|
| 1 | 1976 | 61,797,583,647 |
| 2 | 429 | 14,667,676,567 |
| 3 | 372 | 13,713,658,515 |

### Insight
Product `1976` generated significantly higher transaction volume than all other products.

---

## Product Ownership Validation

A validation check was performed to ensure that each `product_id` belonged to only one team.

### Result
- No abnormal products were detected.
- All products complied with the ownership rule.

### Insight
The product-team mapping was consistent and showed no ownership conflicts.

---

## Lowest Performing Team Since Q2 2023

| Metric | Result |
|---|---|
| Lowest performance team | APS |
| Lowest contributing category | PXXXXXE |

### Insight
Team `APS` recorded the lowest total transaction volume after Q2 2023.

---

## Refund Contribution Analysis

| source_id | Contribution (%) |
|---|---|
| 38 | 59.11% |
| 39 | 26.08% |
| 37 | 14.81% |

### Highest Contributor
- `source_id = 38`

### Insight
`source_id 38` contributed the highest refund transaction volume.

---

## Transaction Type Analysis

Transaction records were classified into:

- Bank Transfer Transaction
- Withdraw Money Transaction
- Top Up Money Transaction
- Payment Transaction
- Transfer Money Transaction
- Split Bill Transaction
- Invalid Transaction

### Insight
The classification transformed raw transaction data into meaningful business transaction categories.

---

## Transaction Summary

| Transaction Type | Transactions | Total Volume |
|---|---|---|
| Payment Transaction | 398,665 | 71,850,608,441 |
| Transfer Money Transaction | 341,173 | 37,032,880,492 |
| Top Up Money Transaction | 290,498 | 108,605,618,829 |
| Bank Transfer Transaction | 37,879 | 50,605,806,190 |
| Withdraw Money Transaction | 33,725 | 23,418,181,420 |
| Split Bill Transaction | 1,376 | 4,901,464 |

### Key Findings

- `Top Up Money Transaction` generated the highest transaction volume.
- `Payment Transaction` had the highest number of transactions.
- `Split Bill Transaction` showed the lowest transaction activity.

---

# Data Quality Checks

| Check | Findings | Action |
|---|---|---|
| Missing values | 49,059 missing values found in the `sender_id` column.<br>164,795 missing values found in the `receiver_id` column.<br>1,317,907 missing values found in the `extra_info` column. | Removed rows with missing values in `sender_id` and `receiver_id` where necessary for transaction analysis. The `extra_info` column was retained since it was not required for the analysis tasks. |

---

# Project Structure

```text
project/
│
├── data/
│   ├── payment_report.csv
│   ├── product.csv
│   └── transactions.csv
│
├── notebooks/
│   └── data_wrangling.ipynb
│
├── README.md
│
└── requirements.txt
```

---

# How to Run

## 1. Install Required Libraries

```bash
pip install pandas numpy
```

## 2. Open Jupyter Notebook

```bash
jupyter notebook
```

## 3. Run the Analysis Notebook

Open:

```text
data_wrangling.ipynb
```

Run all cells to reproduce the analysis and results.
