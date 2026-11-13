Shared retrieval **R1**: Successfully accessed [Apple’s FY2025 Q2 Form 10-Q](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm) using `web__run.open`. A second successful call displayed the remaining balance-sheet rows. All calculations below used JavaScript in `functions.exec`; none were performed without a tool. Exact fractions represent unrounded results.

**SEC-CMP-006**

1. **Retrieve:** R1 above.
2. **Locate:** Part I, Item 1, Condensed Consolidated Statements of Operations, p. 1; “Total net sales”; three-month columns ended March 29, 2025 and March 30, 2024.
3. **Extract:** Respectively **95,359** and **90,753 USD millions**.
4. **Calculate:** Growth = (current − prior) ÷ prior × 100 = (95,359 − 90,753) ÷ 90,753 × 100 = **460,600/90,753%** exactly → **5.08%**.
5. **Report:** Total net sales grew **5.08%**. [Filing](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm)

**SEC-CMP-007**

1. **Retrieve:** R1 above.
2. **Locate:** Part I, Item 1, Statements of Operations, p. 1; operating income and total sales rows; three months ended March 29, 2025.
3. **Extract:** Operating income **29,589**; total net sales **95,359 USD millions**, both for that quarter.
4. **Calculate:** Operating margin = operating income ÷ sales × 100 = 29,589 ÷ 95,359 × 100 = **2,958,900/95,359%** exactly → **31.03%**.
5. **Report:** Consolidated operating margin was **31.03%**. [Filing](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm)

**SEC-CMP-008**

1. **Retrieve:** R1, including the balance-sheet follow-up.
2. **Locate:** Part I, Item 1, Condensed Consolidated Balance Sheets, p. 3; “Total current assets” and “Total current liabilities”; March 29, 2025 column.
3. **Extract:** Current assets **118,674**; current liabilities **144,571 USD millions**, both as of that date.
4. **Calculate:** Current ratio = current assets ÷ current liabilities = **118,674/144,571** exactly → **0.8209**.
5. **Report:** Current ratio was **0.8209:1**. [Filing](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm)

**SEC-CMP-009**

1. **Retrieve:** R1 above.
2. **Locate:** Part I, Item 1, Statements of Operations, p. 1; Services and total sales rows; three months ended March 29, 2025.
3. **Extract:** Services sales **26,645**; total sales **95,359 USD millions**, both for that quarter.
4. **Calculate:** Services share = Services sales ÷ total sales × 100 = 26,645 ÷ 95,359 × 100 = **2,664,500/95,359%** exactly → **27.94%**.
5. **Report:** Services represented **27.94%** of total net sales. [Filing](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm)

**SEC-CMP-010**

1. **Retrieve:** R1 above.
2. **Locate:** Part I, Item 1, Statements of Operations, p. 1; total sales row; six-month and three-month columns ended March 29, 2025.
3. **Extract:** Six-month sales **219,659**; Q2 sales **95,359 USD millions**.
4. **Calculate:** Derived Q1 = six-month sales − Q2 = 219,659 − 95,359 = **124,300 USD millions**, exact. Sequential growth = (Q2 − Q1) ÷ Q1 × 100 = (95,359 − 124,300) ÷ 124,300 × 100 = **−2,894,100/124,300%** exactly → **−23.28%**.
5. **Report:** Derived FY2025 Q1 sales were **124,300 USD millions**; Q2 versus Q1 growth was **−23.28%**. [Filing](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm)