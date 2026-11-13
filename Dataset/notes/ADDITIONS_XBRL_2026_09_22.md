# XBRL additions — September 22, 2026

Added 40 questions: 20 retrieval and 20 computation. There are eight new files, each with five questions. Existing files were not edited. The dataset now has 100 questions: 50 categorized as retrieval and 50 as computation.

## Files and source reports

| Company | Report | Retrieval file | Computation file |
| --- | --- | --- | --- |
| Coca-Cola | FY2025 Q2, ended 2025-06-27 | [xbrl_retrieval_ko_10q.json](../xbrl/retrieval/xbrl_retrieval_ko_10q.json) | [xbrl_compute_ko_10q.json](../xbrl/compute/xbrl_compute_ko_10q.json) |
| PepsiCo | FY2025 Q2, ended 2025-06-14 | [xbrl_retrieval_pep_10q.json](../xbrl/retrieval/xbrl_retrieval_pep_10q.json) | [xbrl_compute_pep_10q.json](../xbrl/compute/xbrl_compute_pep_10q.json) |
| Walmart | FY2026 Q2, ended 2025-07-31 | [xbrl_retrieval_wmt_10q.json](../xbrl/retrieval/xbrl_retrieval_wmt_10q.json) | [xbrl_compute_wmt_10q.json](../xbrl/compute/xbrl_compute_wmt_10q.json) |
| Costco | FY2025 Q3, ended 2025-05-11 | [xbrl_retrieval_cost_10q.json](../xbrl/retrieval/xbrl_retrieval_cost_10q.json) | [xbrl_compute_cost_10q.json](../xbrl/compute/xbrl_compute_cost_10q.json) |

## How these questions were determined

The four companies were absent from the existing datasets. This batch broadens the company coverage to beverage and retail businesses while preserving the prior XBRL focus. All new source reports are 10-Qs; prior 8-K scenarios remain in the dataset.

The tasks were built around actual standard US-GAAP concepts present in SEC company-facts data, rather than assumed tags. Each fact was matched by accession number, form, exact start/end date or instant, and unit. Different companies can use different tags for similar financial concepts.

- Coca-Cola: revenue and taxes, signed operating cash flow, receivables, and dividends; calculations include effective tax rate, cash-flow margin, simple free cash flow, receivables concentration, and derived first-quarter revenue.
- PepsiCo: 12-week revenue and cost of sales, inventory, 24-week cash flow and repurchases; calculations include cost ratio, liabilities/assets, dividend payments relative to cash flow, working capital, and derived first-quarter gross profit.
- Walmart: net sales versus total revenues, inventory, capital purchases, and EPS; calculations include the difference between total revenues and net sales, operating margin, inventory growth, capital spending intensity, and simple free cash flow.
- Costco: 12-week revenue and earnings, 36-week cash flow and dividends, and cash balances; calculations include margins, combined cash distributions, cash-only coverage, and revenue for the first 24 weeks.

These are new company-period questions; familiar formulas intentionally recur. Five questions form a scenario, but are not automatically dependent on one another. Explicit derivations have dependencies within the question. No claim is made that these are complete long-horizon workflows.

## Source verification

Verified on 2026-09-22 against public SEC company-facts API responses. Filing pages were also opened, and the Walmart revenue distinction, Costco reporting durations, PepsiCo week-based periods, and Coca-Cola cash-flow sign were checked against filing text.

### Coca-Cola

- [SEC 10-Q](https://www.sec.gov/Archives/edgar/data/21344/000002134425000061/ko-20250627.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0000021344.json)
- Accession: `0000021344-25-000061`; filed 2025-07-24.
- Quarter: 2025-03-29 through 2025-06-27.
- Year-to-date: 2025-01-01 through 2025-06-27.
- Balance-sheet instant: 2025-06-27.

### PepsiCo

- [SEC 10-Q](https://www.sec.gov/Archives/edgar/data/77476/000007747625000044/pep-20250614.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0000077476.json)
- Accession: `0000077476-25-000044`; filed 2025-07-17.
- Quarter: 2025-03-23 through 2025-06-14.
- Year-to-date: 2024-12-29 through 2025-06-14.
- Balance-sheet instant: 2025-06-14.

### Walmart

- [SEC 10-Q](https://www.sec.gov/Archives/edgar/data/104169/000010416925000137/wmt-20250731.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0000104169.json)
- Accession: `0000104169-25-000137`; filed 2025-08-29.
- Quarter: 2025-05-01 through 2025-07-31.
- Year-to-date: 2025-02-01 through 2025-07-31.
- Balance-sheet instant: 2025-07-31. Inventory-growth computation also uses 2025-01-31.

### Costco

- [SEC 10-Q](https://www.sec.gov/Archives/edgar/data/909832/000090983225000033/cost-20250511.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0000909832.json)
- Accession: `0000909832-25-000033`; filed 2025-06-05.
- Quarter: 2025-02-17 through 2025-05-11.
- Year-to-date: 2024-09-02 through 2025-05-11.
- Balance-sheet instant: 2025-05-11.

## XBRL distinctions tested

1. **Different revenue tags:** Coca-Cola and PepsiCo use `us-gaap:Revenues` here. Walmart's `us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax` represents net sales, while `us-gaap:Revenues` includes membership and other income. The questions specify which measure to use.
2. **Fiscal versus calendar years:** Walmart's July 2025 quarter belongs to FY2026.
3. **Week-based durations:** PepsiCo uses 12-week and 24-week periods here; Costco uses 12-week and 36-week periods. Subtracting Costco's quarter from year-to-date yields the first 24 weeks, not Q1 alone.
4. **Signs:** Coca-Cola's reported operating cash flow is negative. Cash payments represented by payments concepts are treated as positive outflow magnitudes when subtracted.
5. **Units:** SEC API monetary facts are in full USD. Divide by 1,000,000 only when the requested output is USD millions. EPS uses USD/shares; ratios are dimensionless.
6. **Instant versus duration:** Inventories, cash, assets, and liabilities are point-in-time amounts. Income and cash-flow facts span a period.
7. **Exact filing selection:** The same period can appear again in a later filing. Match the specified accession rather than choosing the latest fact or filtering only on fy/fp.

## Validation performed

- All 60 required question-input selections matched the specified concept, accession, form, dates, unit, fiscal year/period, and filing date in the SEC API.
- No conflicting values were found for a selected input.
- All 20 computation formulas were evaluated as arithmetic sanity checks; denominators were nonzero and results finite.
- Confirmed 20 retrieval and 20 computation additions, five questions per file, and the original 16-field format.
- Confirmed unique question IDs and exact question text across all 100 records.
- New IDs run XBRL-RET-016 through XBRL-RET-035 and XBRL-CMP-016 through XBRL-CMP-035. Scenario suffixes are 004–007.

Answer fields remain descriptive placeholders. Computed sanity-check results are not delivered as an answer key. No agent was run and edgartools compatibility was not tested.

## Field conventions

The format follows the previous batch. `xbrl_concepts`, dates, filing identifiers, and units are grounded in SEC data. Questions, formulas, placeholders, and evidence descriptions were authored from those verified inputs.

`hops` is an author-assigned task-depth estimate: 1 for retrieval; 2 for retrieving inputs and applying a formula; 3 for multi-period derivation or comparison. It is not a measured tool-call count.

`workflow_step` gives order within a five-question group. `reasoning` contains an author-written solution guide. `tool_required` retains the template's edgartools capability convention, rather than asserting a tested runtime.

A future evaluator should hide answer placeholders and solution reasoning from the agent, decide whether concept/source hints are visible, independently review reference answers, and reset state between independently evaluated scenarios.

