# Data Anomaly Audit

Automated anomaly detection on U.S. federal government financial datasets sourced from the **U.S. Treasury Fiscal Data API**.

## What This Is

An audit of 5 government financial datasets (4,500+ records) to surface unusual patterns, outliers, and noteworthy data points in federal spending, debt, revenue, interest rates, and budgets. **22 anomalies** were identified and ranked by significance.

## Highlights

- **$494B single-month outlay** in Commerce and Housing Credit (PPP/CARES Act, June 2020)
- **$358B overnight debt jump** when the 2023 debt ceiling was lifted
- **$452B monthly stimulus spike** in Income Security (March 2021)
- **$58.5B FDIC emergency outlays** from 2023 bank failures (SVB, Signature, First Republic)
- **121x increase in Treasury Bill rates** (0.045% to 5.451%) during the Fed hiking cycle
- **Zombie appropriations** still on the books -- Andean Counterdrug Programs at $160.60

## Project Structure

```
.
├── README.md
├── anomalies_report.md          # Full ranked anomaly report (22 findings)
├── data/                        # Raw datasets (stored via Git LFS)
│   ├── federal_spending_by_agency.csv
│   ├── federal_debt_daily.csv
│   ├── federal_receipts_by_source.csv
│   ├── federal_interest_rates.csv
│   ├── federal_budget_summary.csv
│   └── federal_trust_fund_receipts.csv
└── analysis/                    # Per-dataset analysis notes
    ├── spending_analysis.txt
    ├── debt_analysis.txt
    ├── receipts_analysis.txt
    ├── interest_analysis.txt
    └── budget_analysis.txt
```

## Datasets

| Dataset | Source | Period | Records |
|---------|--------|--------|---------|
| [Federal Spending by Agency](data/federal_spending_by_agency.csv) | MTS Table 5 | Jan 2024 (FY2024 FYTD) | 500 |
| [Federal Debt Daily](data/federal_debt_daily.csv) | Debt to the Penny | Mar 2022 -- Mar 2026 | 1,000 |
| [Federal Receipts by Source](data/federal_receipts_by_source.csv) | MTS Table 4 | Jan 2020 -- Sep 2021 | 1,000 |
| [Federal Interest Rates](data/federal_interest_rates.csv) | Avg Interest Rates on Treasury Securities | Apr 2021 -- Feb 2026 | 1,000 |
| [Federal Budget Summary](data/federal_budget_summary.csv) | MTS Table 9 | Jan 2020 -- Aug 2022 | 1,000 |

All data sourced from the [U.S. Treasury Fiscal Data API](https://fiscaldata.treasury.gov/).

## Key Themes

1. **COVID-19 Emergency Spending** -- The pandemic created the most dramatic anomalies across every dataset
2. **Debt Ceiling Politics** -- Two distinct episodes (2023, 2025) produced $350B+ overnight debt jumps
3. **Interest Cost Explosion** -- T-Bill rates rose 121x, pushing annualized interest costs above $1 trillion
4. **Structural Fiscal Shifts** -- Government increasingly dependent on market borrowing vs. trust fund surpluses
5. **Accounting Artifacts** -- Many dramatic data points are bookkeeping conventions, not real fiscal events

## How to Read

Start with [`anomalies_report.md`](anomalies_report.md) for the full ranked list of 22 anomalies. Each entry includes specific data points, causes, and context. Individual dataset analyses are in the [`analysis/`](analysis/) folder.

## Data Storage

CSV files are stored using **Git LFS**. To clone with data:

```bash
git lfs install
git clone git@github.com:Ritesh17rb/data-anomaly-audit.git
```

## License

Data is public domain (U.S. government works). Analysis is provided as-is for informational purposes.
