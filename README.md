# Data Ingestion, Cleaning & Preprocessing with Pandas

Cleans a messy, real-world retail sales dataset (10,800 raw rows) containing
missing values, duplicate records, and inconsistent data types.

## Files

| File | Description |
|---|---|
| `data_cleaning_pandas.ipynb` | Jupyter Notebook with the full ingestion → cleaning → feature engineering → export pipeline (already executed, outputs included) |
| `raw_retail_sales.csv` | Raw, messy input dataset (10,800 rows) |
| `clean_dataset.csv` | Final cleaned & standardized output (10,395 rows, 0 missing values, 0 duplicates) |

## What the notebook does

1. **Load** the raw dataset into Pandas
2. **Audit** — profile missing values, duplicates, dtypes, and inconsistent category labels
3. **Clean**
   - Drop exact and `OrderID` duplicates
   - Standardize text casing/whitespace (Category, Region, PaymentMethod, Channel, Product)
   - Strip stray characters (`$`, trailing spaces) from `Quantity` / `UnitPrice` and cast to numeric
   - Parse 4 mixed date formats in `OrderDate` into a single `datetime` column
4. **Handle outliers** — invalid `CustomerAge` values nulled out; `Revenue` outliers capped via the IQR method
5. **Impute missing values** — mode for categorical columns, median for numeric columns, drop rows with unparseable dates
6. **Feature engineering**
   - `OrderYear`, `OrderMonth`, `OrderMonthName` extracted from `OrderDate`
   - `TotalCost`, `Profit`, `ProfitMarginPct` calculated from cleaned price/quantity fields
7. **Validate** — confirm 0 missing values and 0 duplicates remain
8. **Export** the clean dataset to `clean_dataset.csv`

## How to run

```bash
pip install pandas numpy jupyter
jupyter notebook data_cleaning_pandas.ipynb
```
