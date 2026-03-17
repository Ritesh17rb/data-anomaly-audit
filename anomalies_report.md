# Government Financial Data Anomaly Report

> **Generated**: March 17, 2026
> **Datasets Analyzed**: 5 US Treasury datasets (4,500+ records)
> **Source**: US Treasury Fiscal Data API (`fiscaldata.treasury.gov`)
> **Methodology**: Automated anomaly detection across spending, debt, revenue, interest rates, and budget summary data

---

## Datasets Overview

| # | Dataset | Source Table | Period | Records | File |
|---|---------|-------------|--------|---------|------|
| 1 | Federal Spending by Agency | MTS Table 5 | Jan 2024 (FY2024 FYTD) | 500 | [federal_spending_by_agency.csv](data/federal_spending_by_agency.csv) |
| 2 | Federal Debt Daily | Debt to the Penny | Mar 2022 -- Mar 2026 | 1,000 | [federal_debt_daily.csv](data/federal_debt_daily.csv) |
| 3 | Federal Receipts by Source | MTS Table 4 | Jan 2020 -- Sep 2021 | 1,000 | [federal_receipts_by_source.csv](data/federal_receipts_by_source.csv) |
| 4 | Federal Interest Rates | Avg Interest Rates on Treasury Securities | Apr 2021 -- Feb 2026 | 1,000 | [federal_interest_rates.csv](data/federal_interest_rates.csv) |
| 5 | Federal Budget Summary | MTS Table 9 | Jan 2020 -- Aug 2022 | 1,000 | [federal_budget_summary.csv](data/federal_budget_summary.csv) |

---

## All Anomalies Ranked by Significance

### #1 -- Commerce and Housing Credit: $494 Billion Single-Month Outlay (June 2020)
**Dataset**: Federal Budget Summary (MTS Table 9)
**Severity**: Extreme

Commerce and Housing Credit recorded a **single-month outlay of $494.3 billion** in June 2020. This category typically runs $1--6 billion per month. The prior fiscal year FYTD was **negative $26.9 billion** (net inflow), while the current FYTD exploded to **$528.0 billion** -- a swing of ~$555 billion year-over-year.

- **Cause**: Paycheck Protection Program (PPP) and CARES Act lending programs
- **By FY2020 year-end**: FYTD reached **$571.7B** vs. prior year's **-$26.1B** (net swing of ~$598 billion)
- **Data points**: `2020-06-30, Commerce and Housing Credit, current_month=$494.3B, current_fytd=$528.0B, prior_fytd=-$26.9B`

---

### #2 -- 2023 Debt Ceiling Release: $358 Billion in One Weekend
**Dataset**: Federal Debt Daily (Debt to the Penny)
**Severity**: Extreme

Between June 2 and June 5, 2023, total federal debt jumped from **$31,467B to $31,826B** -- a **$358.6 billion increase** over a single weekend. This was the largest single-record increase in the entire 4-year dataset.

- **Cause**: Resolution of the 2023 debt ceiling crisis (Fiscal Responsibility Act signed June 3, 2023)
- **Context**: Total debt had been frozen around ~$31,457--31,467B for months (Jan--May 2023) during the ceiling standoff
- **Public debt surged** $24,702B to $25,032B (+$330B) as Treasury issued massive new debt to rebuild cash reserves
- **Data points**: `2023-06-02: $31,467,099,921,028 -> 2023-06-05: $31,825,678,823,229`

---

### #3 -- Income Security: $307 Billion Single Month, then $452 Billion (COVID Stimulus)
**Dataset**: Federal Budget Summary (MTS Table 9)
**Severity**: Extreme

Income Security outlays in **April 2020 hit $307.2 billion**, roughly **7x the normal $39--46B monthly run rate**. The FY2020 total reached **$1.263 trillion** vs. prior year's **$515.4 billion** (+145%).

An even larger spike came in **March 2021 at $452.6 billion** (American Rescue Plan stimulus checks and extended unemployment), pushing FY2021 to **$1.649 trillion**.

- **Cause**: CARES Act stimulus payments, enhanced unemployment benefits, American Rescue Plan
- **Context**: April 2020 single-month figure alone exceeded many countries' entire annual budgets

---

### #4 -- FDIC Deposit Insurance Fund: $58.5 Billion in Emergency Outlays
**Dataset**: Federal Spending by Agency (MTS Table 5)
**Severity**: Very High

The FDIC Deposit Insurance Fund shows **$58.5 billion in FYTD net outlays** through January 2024. In normal years, FDIC net outlays are near zero or negative (funded by insurance premiums).

- **Cause**: Aftermath of March 2023 bank failures (Silicon Valley Bank, Signature Bank, First Republic Bank) -- FDIC invoked systemic risk exception
- **Context**: This single line item exceeds the entire Department of Education's FYTD spending ($57.3B)
- **Data point**: `2024-01-31, Deposit Insurance Fund: $58,540,365,877.14`

---

### #5 -- Massive FICA Adjustment: $44 Billion Single-Month Reversal (June 2021)
**Dataset**: Federal Receipts by Source (MTS Table 4)
**Severity**: Very High

In June 2021, "Adjustments Attributable to Prior Years-FICA" recorded **-$43,986,300,615.84** -- a negative $44 billion in a single month. This flipped the FYTD from positive to **-$38.0 billion**, vs. the prior year's **+$8.4 billion** -- a $46 billion swing.

- **Cause**: Retroactive correction related to COVID-era payroll tax deferrals (CARES Act allowed employers to defer Social Security taxes from Mar--Dec 2020)
- **Context**: Largest single negative line-item movement in the receipts dataset

---

### #6 -- Interest on Public Debt: $357 Billion in Just 4 Months
**Dataset**: Federal Spending by Agency (MTS Table 5)
**Severity**: Very High

Through the first 4 months of FY2024, gross interest on Treasury debt reached **$357.2 billion**. Annualized, this implies ~**$1.07 trillion** for the full fiscal year.

- **Composition**: $273.7B on public issues (accrual) + $83.5B on special issues (cash)
- **Context**: This 4-month interest bill alone exceeds every department's FYTD spending except HHS and Social Security
- **Trend**: Interest costs have roughly doubled in a few years due to rising rates
- **Data point**: `2024-01-31, Total--Interest on Treasury Debt Securities (Gross): $357,206,848,711.31`

---

### #7 -- Debt Ceiling 2025: Total Debt Flatlines for ~4 Months
**Dataset**: Federal Debt Daily (Debt to the Penny)
**Severity**: High

From approximately late March through early July 2025, total public debt barely moved, hovering in a ~$5 billion band around **$36,213--36,218 billion**. Normal daily swings are $20--60 billion. Meanwhile, the subcomponents (public debt and intragovernmental holdings) swung $20--40 billion daily in **opposite directions**.

- **Cause**: Statutory debt ceiling was binding; Treasury used extraordinary measures
- **Resolution**: July 3--7, 2025 saw a **$366.4 billion jump** when the ceiling was lifted (pent-up borrowing released over July 4th weekend)

| Date | Total Debt | Notes |
|------|-----------|-------|
| 2025-04-01 | $36,215,156,673,113 | Ceiling binding |
| 2025-06-30 | $36,211,469,351,821 | Still frozen |
| 2025-07-07 | $36,582,313,190,019 | +$366B post-ceiling |

---

### #8 -- General Government: $144.9 Billion Spike (74x Normal)
**Dataset**: Federal Budget Summary (MTS Table 9)
**Severity**: High

General Government outlays are typically $1--5 billion per month. In **April 2020, spending spiked to $144.9 billion** -- roughly **74x the baseline**.

- **Cause**: Economic Impact Payments (stimulus checks) administered by Treasury/IRS
- **Recurrence**: May 2021 at $132.1B and June 2021 at $68.2B (third-round checks under the American Rescue Plan)
- **Context**: Highest spike-to-baseline ratio of any category in the dataset

---

### #9 -- I Bonds (Savings Inflation Securities) Hit 10.251%
**Dataset**: Federal Interest Rates
**Severity**: High

US Savings Inflation Securities (I Bonds) reached a peak average rate of **10.251% in September 2022** -- the highest rate for any actively-traded security type in the dataset.

| Date | Rate |
|------|------|
| Apr 2021 | 3.425% |
| May 2022 | 8.911% |
| Sep 2022 | **10.251%** (peak) |
| Oct 2022 | 7.688% (anomalous dip) |
| Nov 2022 | 10.148% (recovery) |
| Feb 2026 | 4.248% |

- **Cause**: I Bond composite rate tracks CPI inflation, which peaked mid-2022
- **Sub-anomaly**: The October 2022 dip to 7.688% between two ~10% months reflects semi-annual rate reset timing

---

### #10 -- SBA Intrabudgetary Transactions: Negative $169.8 Billion
**Dataset**: Federal Spending by Agency (MTS Table 5)
**Severity**: High

The Small Business Administration shows **-$169.8 billion in intrabudgetary transactions**, yet its total net outlays are only $660.7 million.

- **Cause**: Unwinding/repayment of pandemic-era PPP and EIDL intergovernmental transfers
- **Context**: This is the largest single negative line item in the entire spending dataset -- a $170B accounting offset at an agency with just $661M in net spending

---

### #11 -- Treasury Bills: 121x Interest Rate Increase
**Dataset**: Federal Interest Rates
**Severity**: High

Treasury Bills went from **0.045% (June 2021)** to **5.451% (November 2023)** -- a factor of **121x** increase.

| Date | T-Bill Rate |
|------|-----------|
| Jun 2021 | 0.045% |
| Jun 2022 | 1.073% |
| Dec 2022 | 3.891% |
| Nov 2023 | **5.451%** (peak) |
| Feb 2026 | 3.720% |

- **Comparison**: Treasury Bonds only moved from ~3.0% to ~3.4% over the same period
- **Context**: Reflects the Fed's aggressive rate hiking cycle and classic yield curve inversion dynamics

---

### #12 -- COVID Collapse of Airport Trust Fund: Revenue Goes Negative
**Dataset**: Federal Receipts by Source (MTS Table 4)
**Severity**: High

The Airport and Airway Trust Fund (funded by airline ticket taxes) went from **$2.85B (Feb 2020)** to **-$571M (May 2020)** -- revenue went *negative* as refunds exceeded new collections.

| Month | Revenue |
|-------|---------|
| Feb 2020 | $2,854,352,418 |
| Apr 2020 | $661,931,000 |
| May 2020 | **-$571,489,462** |
| Jun 2020 | $7,713,000 |
| Jul 2020 | $13,464,000 |
| FY2020 FYTD | $9.0B vs. prior $16.0B (-44%) |

- **Cause**: Near-total shutdown of air travel during COVID lockdowns
- **Context**: Five consecutive months of effectively zero (or negative) revenue

---

### #13 -- Corporation Income Tax: COVID Drop Then 75.5% Surge
**Dataset**: Federal Receipts by Source (MTS Table 4)
**Severity**: Moderate

Corporate tax revenue dropped 8% in FY2020 ($211.8B vs. $230.2B), then **surged 75.5% in FY2021** to $371.8B -- the single largest year-over-year percentage increase for any major revenue category.

- **Peak month**: September 2021 at **$86.7B** (highest single month in the dataset)
- **Negative months**: Feb 2020 (-$2.0B), May 2020 (-$1.8B), Nov 2020 (-$3.2B) -- refunds exceeded collections
- **Context**: Reflects corporate profit boom during economic recovery

---

### #14 -- Foreign Series Securities: 7.312% to 0.000% Overnight
**Dataset**: Federal Interest Rates
**Severity**: Moderate

The "Foreign Series" non-marketable security held a perfectly flat **7.312%** for 23 consecutive months (Apr 2021--Feb 2023), then dropped to exactly **0.000%** in March 2023 and stayed there for the remaining 35 months.

- **Cause**: Likely maturity/retirement of the last outstanding Foreign Series obligations
- **Data issue**: 0.000% is ambiguous -- could mean zero-rate debt or no debt outstanding

---

### #15 -- Domestic Series: Frozen at 7.577% for 59 Straight Months
**Dataset**: Federal Interest Rates
**Severity**: Moderate

The "Domestic Series" rate is exactly **7.577%** in every single month from April 2021 through February 2026 -- never changing once. This is the highest persistent rate in the dataset, more than double typical marketable security rates.

- **Context**: Legacy obligations from a higher interest rate era; the government pays 7.577% on this while issuing new T-Bills at rates as low as 0.045%

---

### #16 -- Fiscal Year-End Accounting Jumps: $200--275 Billion Overnight
**Dataset**: Federal Debt Daily (Debt to the Penny)
**Severity**: Moderate

Every fiscal year boundary (September 30 to October 1) shows dramatic overnight debt jumps:

| Transition | Jump |
|-----------|------|
| FY2023 (Sep 29 -- Oct 2, 2023) | **+$274.8 billion** |
| FY2025 (Sep 30 -- Oct 1, 2025) | **+$226.5 billion** |
| FY2024 (Sep 30 -- Oct 1, 2024) | **+$204.3 billion** |

- **Cause**: End-of-year accounting adjustments in intragovernmental trust fund accounts (Social Security, Medicare, federal retirement)
- **Context**: Almost entirely bookkeeping artifacts in the intragov column, not new public borrowing

---

### #17 -- Intragovernmental Holdings Ratio Declining Over Time
**Dataset**: Federal Debt Daily (Debt to the Penny)
**Severity**: Moderate

Intragovernmental holdings as a share of total debt is structurally declining:

| Date | Intragov Share |
|------|---------------|
| Mar 2022 | 21.4% ($6,496B of $30,282B) |
| Oct 2024 | 20.6% ($7,357B of $35,668B) |
| Mar 2026 | 19.5% ($7,602B of $38,903B) |

- **Key stat**: ~87% of all new debt was issued to the public (markets), not to trust funds
- **Implication**: Government increasingly dependent on market financing, with implications for interest costs and market absorption capacity

---

### #18 -- Federal Reserve Remittances Surged 55% During COVID
**Dataset**: Federal Receipts by Source (MTS Table 4)
**Severity**: Moderate

Fed remittances to Treasury jumped from $52.8B (FY2019) to **$81.9B (FY2020)** -- up 55% -- while most other revenue sources fell.

- **Cause**: Fed's balance sheet expanded from ~$4T to ~$8T through quantitative easing, generating higher interest income remitted to Treasury
- **Context**: Counter-cyclical pattern -- the Fed's emergency actions effectively generated tens of billions in additional Treasury revenue

---

### #19 -- Excise Tax Collapse: 95% Single-Month Drop
**Dataset**: Federal Budget Summary (MTS Table 9)
**Severity**: Moderate

Excise taxes plummeted to **$353 million in April 2020** -- a **95% decline** from the typical $6--7 billion monthly level.

- **FY2020 full year**: $86.8B vs. prior $98.9B (-12%)
- **Pre-COVID anomaly**: January 2020 already showed Miscellaneous Excise Taxes 55% below prior year FYTD, likely from repeal of ACA health insurance tax (structural, not COVID-related)
- **Recovery**: Did not reach prior-year levels until FY2022

---

### #20 -- Zombie Appropriations: Micro-Dollar Line Items Still Active
**Dataset**: Federal Spending by Agency (MTS Table 5)
**Severity**: Low (but interesting)

Several budget lines show absurdly small amounts suggesting dormant programs never formally closed:

| Program | FYTD Amount |
|---------|------------|
| Andean Counterdrug Programs | **$160.60** |
| USDA Supplemental Assistance | $4,077.93 |
| Veterans Choice Fund | $71,302.06 |
| Formula Grants (Federal Transit) | $127,225.00 |
| Amtrak Capital & Debt Service Grants | $76,352.23 |

- **Context**: The Andean Counterdrug Programs at $160.60 is particularly striking -- a Cold War/War on Drugs-era program still processing transactions measured in hundreds of dollars

---

### #21 -- Net Interest Goes Negative in September (Year-End Reversals)
**Dataset**: Federal Budget Summary (MTS Table 9)
**Severity**: Low

Net Interest went **negative** in two fiscal year-end months:
- September 2020: **-$1.26 billion**
- September 2021: **-$5.94 billion**

- **Cause**: Fiscal year-end accrual reversals/adjustments
- **Context**: Full-year FY2020 net interest actually *declined* despite dramatically higher debt, reflecting the sharp drop in interest rates

---

### #22 -- Payment to Military Retirement Fund: Suspiciously Round Number
**Dataset**: Federal Spending by Agency (MTS Table 5)
**Severity**: Low (data quality note)

The payment to the Military Retirement Fund is exactly **$151,521,000,000.00** -- a perfectly round number to the dollar.

- **Explanation**: This is a calculated mandatory transfer, not actual disbursements
- **Issue**: Its inclusion inflates "Other Defense Civil Programs" totals and can mislead spending analysis

---

## Data Quality Issues Summary

| Dataset | Issue | Impact |
|---------|-------|--------|
| Spending by Agency | "null" strings instead of proper nulls for 34 category headers | Low -- parseable with filtering |
| Spending by Agency | Missing "Total" roll-ups for some sections (e.g., Independent Agencies) | Moderate -- inconsistent aggregation |
| Spending by Agency | Single time period only (Jan 2024) -- no trend analysis possible | High -- limits analytical value |
| Debt Daily | Debt ceiling periods artificially suppress headline numbers | Moderate -- known distortion |
| Receipts by Source | Truncated September 2021 data (missing Total lines) | High -- incomplete fiscal year |
| Receipts by Source | Typo: "Attrbutable" (missing 'i') in SECA adjustment field | Low -- cosmetic |
| Receipts by Source | Minor FYTD continuity discrepancy ($1,141 on $3 trillion) | Negligible |
| Interest Rates | Missing 3 records for April 2021 (T-Bills, totals) | Moderate -- gaps in earliest month |
| Interest Rates | 0.000% ambiguous (zero rate vs. no outstanding balance) | Moderate -- interpretation issue |
| Budget Summary | ~90 "null" rows are section headers, not data | Low -- parseable with filtering |
| Budget Summary | Dataset ends mid-FY2022 (Aug 2022, missing Sept) | Moderate -- incomplete year |
| All datasets | Amounts stored as quoted strings including "null" | Low -- requires type conversion |

---

## Key Themes Across All Datasets

1. **COVID-19 Emergency Spending Dominance**: The pandemic created the most dramatic anomalies across every dataset -- from $494B single-month outlays to near-zero airport revenue to $44B FICA adjustment reversals.

2. **Debt Ceiling Political Theater**: Two distinct debt ceiling episodes (2023 and 2025) produced the most dramatic single-day changes in debt data, with $358B and $366B overnight jumps when limits were lifted.

3. **Interest Cost Explosion**: Treasury Bill rates increased 121x (0.045% to 5.451%), driving annualized interest costs above $1 trillion -- now rivaling the largest mandatory spending programs.

4. **Structural Fiscal Shifts**: The declining ratio of intragovernmental holdings (21.4% to 19.5%) means the government is increasingly dependent on market borrowing, not trust fund surpluses.

5. **Accounting Artifacts**: Many dramatic-looking data points (fiscal year-end jumps, negative net interest months, "null" category headers) are accounting conventions rather than real fiscal events -- highlighting the importance of domain knowledge when interpreting government financial data.

---

*Data sourced from the US Treasury Fiscal Data API (`api.fiscaldata.treasury.gov`). All amounts in USD. Analysis performed on raw CSV data without modification.*
