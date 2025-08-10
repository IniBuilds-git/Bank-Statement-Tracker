# Personal Finance Tracker

A Jupyter Notebook project for tracking income, expenses, and savings.  
It processes a bank transaction CSV, categorizes entries, calculates financial summaries, and generates monthly visual charts.

---

## Overview

This project:
- Reads and cleans bank transaction data.
- Categorizes transactions into useful groups (Salary, UPI Payments, Bank Charges, etc.).
- Calculates:
  - Total income
  - Total expenses
  - Net savings
  - Savings rate (%)
- Generates:
  - Monthly income vs. expenses trend chart
  - Monthly net savings bar chart

---

## Requirements

- Python 3.8+ (Anaconda recommended)
- Jupyter Notebook
- Install dependencies:
  ```bash
  pip install pandas numpy matplotlib
  ```

---

## Data Format

Your CSV file should contain at least:
- **Date** – transaction date
- **DrCr** – `Cr` for credit, `Db` for debit
- **amount** – numeric transaction value
- **mode** – payment mode (e.g., UPI, NEFT)
- **name** – optional transaction description

Dates should be in `YYYY-MM-DD` format or adjusted in the notebook.

---

## How to Use

1. **Clone or download** this repository.
2. **Place your CSV file** in the same folder as `tracker.ipynb`.
3. Open the notebook:
   ```bash
   jupyter notebook tracker.ipynb
   ```
4. Update the CSV path in the first cell.
5. Run all cells (`Kernel → Restart & Run All`).
6. View printed summaries and generated charts.

---

## How It Works

1. **Load CSV** using `pandas`.
2. **Clean & Normalize** column names and data types.
3. **Create Signed Amount**:
   ```python
   df['signed_amount'] = np.where(df['DrCr'] == 'Cr', df['amount'], -df['amount'])
   ```
4. **Categorize Transactions**  
   Using a custom function, classify each row into categories like:
   - Salary/Income
   - Digital Payments
   - Bank Charges
   - Investments
5. **Monthly Summary**  
   Group by `month_year` to calculate:
   - Net amount
   - Transaction count
   - Average transaction value
6. **Visualizations**  
   - **Line chart**: Income vs. Expenses over time
   - **Bar chart**: Net Savings (green = positive, red = negative)
   - **Category breakdown** table

---

## Example Output

**Printed Summary**
```
Total Income: 1,200,000
Total Expenses: 900,000
Net Savings: 300,000
Savings Rate: 25.0%
```

**Charts**
- Monthly income vs. expenses
- Net savings by month
- Spending by category

---

## Notes
- If column names differ, rename them in the code before processing.
- If your dates are not in `YYYY-MM-DD` format, adjust `pd.to_datetime()` parsing.
- `month_year` is extracted for grouping as `YYYY-MM`.

---

## License
MIT License
