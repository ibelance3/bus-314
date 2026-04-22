# stage3-spec-Ibe.md

## **1\. Problem Statement**

This model evaluates the financial performance of Apple over FY2024 and FY2023 using ratio analysis across profitability, efficiency, liquidity, leverage, and market value.

The goal is to:

* Convert raw financial statements into standardized metrics  
* Enable year-over-year comparison  
* Support financial decision-making

**2\. Workbook Structure** 

Create **5 Excel sheets exactly named:**

1. **Balance\_Sheet**  
2. **Income\_Statement**  
3. **Cash\_Flow**  
4. **Assumptions**  
5. **Ratios**

**3\. Sheet Layouts (EXACT FORMAT)**

### **Balance\_Sheet Tab**

| Column A | Column B | Column C |
| ----- | ----- | ----- |
| Account Name | FY2024 | FY2023 |

Example rows:

* A2: Cash and Cash Equivalents  
* A3: Accounts Receivable  
* A4: Inventory  
* A5: Total Current Assets  
* A6: Total Assets  
* A7: Total Current Liabilities  
* A8: Total Liabilities  
* A9: Shareholders’ Equity

**Income\_Statement Tab**

| Column A | Column B |
| ----- | ----- |
| Account Name | FY2024 |

Rows:

* Revenue  
* COGS  
* EBIT  
* Interest Expense  
* Net Income

**Cash\_Flow Tab**

| Column A | Column B |
| ----- | ----- |
| Operating Cash Flow | FY2024 |
| CapEx | FY2024 |

**Assumptions Tab**

| Variable | Value |
| ----- | ----- |
| Tax Rate | 0.21 |
| WACC | (input value) |
| Share Price | (input) |
| Shares Outstanding | (input) |

**4\. Named Ranges** 

Define these in Excel:

* BAL\_total\_assets\_2024 \= Balance\_Sheet\!B6  
* BAL\_total\_assets\_2023 \= Balance\_Sheet\!C6  
* BAL\_equity\_2024 \= Balance\_Sheet\!B9  
* BAL\_equity\_2023 \= Balance\_Sheet\!C9  
* BAL\_inventory\_2024 \= Balance\_Sheet\!B4  
* BAL\_inventory\_2023 \= Balance\_Sheet\!C4  
* BAL\_ar\_2024 \= Balance\_Sheet\!B3  
* BAL\_ar\_2023 \= Balance\_Sheet\!C3  
* BAL\_current\_assets\_2024 \= B5  
* BAL\_current\_liabilities\_2024 \= B7

Income:

* INC\_sales \= Income\_Statement\!B2  
* INC\_cogs \= B3  
* INC\_ebit \= B4  
* INC\_interest \= B5  
* INC\_net\_income \= B6

**5\. Step-by-Step Build Instructions (NO GUESSING)**

### **Step 1: Input Data**

* Enter all financial data manually into each sheet  
* Do NOT hardcode numbers in formulas

**Step 2: Create Ratios Sheet**

| Metric | Formula |
| :---: | :---: |

**Step 3: Derived Inputs (Exact Excel Formulas)**

* Avg Assets:  
   \=(BAL\_total\_assets\_2024 \+ BAL\_total\_assets\_2023)/2  
* Avg Equity:  
   \=(BAL\_equity\_2024 \+ BAL\_equity\_2023)/2  
* Avg Inventory:  
   \=(BAL\_inventory\_2024 \+ BAL\_inventory\_2023)/2  
* Avg AR:  
   \=(BAL\_ar\_2024 \+ BAL\_ar\_2023)/2  
* NOPAT:  
   \=INC\_ebit\*(1-Assumptions\!B1)  
* Invested Capital:  
   \=BAL\_total\_assets\_2024 \- BAL\_current\_liabilities\_2024

**6\. Ratio Calculations (EXACT FORMULAS)**

### **Profitability**

* ROA:  
   \=INC\_net\_income / Avg\_Assets  
* ROE:  
   \=INC\_net\_income / Avg\_Equity  
* ROC:  
   \=NOPAT / Invested\_Capital

**Efficiency**

* Asset Turnover:  
   \=INC\_sales / Avg\_Assets  
* Inventory Turnover:  
   \=INC\_cogs / Avg\_Inventory  
* Days Inventory:  
   \=365 / Inventory\_Turnover  
* Receivables Turnover:  
   \=INC\_sales / Avg\_AR  
* Collection Period:  
   \=365 / Receivables\_Turnover

**Liquidity**

* Current Ratio:  
   \=BAL\_current\_assets\_2024 / BAL\_current\_liabilities\_2024  
* Quick Ratio:  
   \=(BAL\_current\_assets\_2024 \- BAL\_inventory\_2024) / BAL\_current\_liabilities\_2024  
* Cash Ratio:  
   \=BAL\_cash\_2024 / BAL\_current\_liabilities\_2024

**Leverage**

* Debt Ratio:  
   \=BAL\_total\_liabilities\_2024 / BAL\_total\_assets\_2024  
* Debt to Equity:  
   \=BAL\_total\_liabilities\_2024 / BAL\_equity\_2024  
* Interest Coverage:  
   \=INC\_ebit / INC\_interest

**Market Metrics**

* Market Cap:  
   \=Assumptions\!B3 \* Assumptions\!B4  
* Market-to-Book:  
   \=Market\_Cap / BAL\_equity\_2024  
* EVA:  
   \=NOPAT \- (Assumptions\!B2 \* Invested\_Capital)

**DuPont**

* Profit Margin:  
   \=INC\_net\_income / INC\_sales  
* Equity Multiplier:  
   \=Avg\_Assets / Avg\_Equity  
* ROE Check:  
   \=Profit\_Margin \* Asset\_Turnover \* Equity\_Multiplier

**7\. Outputs (FINAL MODEL VIEW)**

The Ratios tab should include:

* All ratios listed in a table  
* Separate sections:  
  * Profitability  
  * Efficiency  
  * Liquidity  
  * Leverage  
  * Market

Optional:

* Add charts comparing ratios

**8\. Validation (NEW — IMPORTANT ADDITION)**

Add error checks:

* If denominator \= 0 → return “N/A”  
   Example:  
   \=IF(BAL\_current\_liabilities\_2024=0,"N/A",BAL\_current\_assets\_2024/BAL\_current\_liabilities\_2024)

**9\. Improvements Over Original Spec**

What was fixed from your version :

* Added **exact sheet structure**  
* Added **cell-level instructions**  
* Converted all formulas to **Excel format**  
* Eliminated ambiguity  
* Added **step-by-step build process**  
* Added **error handling \+ validation**

