# XBRL dataset expansion — September 18, 2026

## Added files

| File | Scenario | Questions |
| --- | --- | --- |
| xbrl_retrieval_tsla_10q.json | Tesla FY2025 Q2 | 5 retrieval |
| xbrl_compute_tsla_10q.json | Tesla FY2025 Q2 | 5 computation |
| xbrl_retrieval_amd_10q.json | AMD FY2025 Q2 | 5 retrieval |
| xbrl_compute_amd_10q.json | AMD FY2025 Q2 | 5 computation |

All 20 new questions preserve the original 16-field structure and symbolic answer placeholders. Existing datasets were not edited. The folder now contains 60 questions: 30 categorized as retrieval and 30 as computation.

## How the scenarios were selected

Tesla and AMD were absent from the existing eight files. Their Q2 10-Qs provide multiple reporting durations, balance-sheet instants, and machine-readable US-GAAP facts. These let the benchmark test XBRL context selection as well as arithmetic.

Tesla covers quarterly revenue, EPS, inventory, year-to-date operating cash flow, and R&D; calculations cover margins, R&D intensity, task-defined free cash flow, working capital, and deriving Q1 operating income.

AMD covers a signed quarterly operating result, cash, year-to-date capital purchases, gross profit, and current liabilities; calculations cover inventory concentration, explicitly defined cash-only coverage, signed operating margin, capital purchases relative to cash flow, and deriving Q1 gross profit before computing sequential growth.

These are new company/period questions, not claims that every financial formula is new. Some formulas intentionally recur across companies. This batch focuses on 10-Q XBRL; the earlier NVIDIA 8-K questions remain available.

## SEC source verification

The raw filing download for Tesla returned HTTP 403. Verification therefore used SEC's company-facts API to inspect actual reported tags, units, accession numbers, dates, and numeric facts. The filing pages were also opened through web browsing. No non-SEC source is used by these datasets.

### TSLA

- [SEC filing](https://www.sec.gov/Archives/edgar/data/1318605/000162828025035806/tsla-20250630.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0001318605.json)
- Accession: `0001628280-25-035806`; filing date: 2025-07-24.
- Quarterly duration: 2025-04-01 through 2025-06-30.
- Year-to-date duration: 2025-01-01 through 2025-06-30.
- Balance-sheet instant: 2025-06-30.

### AMD

- [SEC filing](https://www.sec.gov/Archives/edgar/data/2488/000000248825000108/amd-20250628.htm)
- [SEC XBRL company facts](https://data.sec.gov/api/xbrl/companyfacts/CIK0000002488.json)
- Accession: `0000002488-25-000108`; filing date: 2025-08-06.
- Quarterly duration: 2025-03-30 through 2025-06-28.
- Year-to-date duration: 2024-12-29 through 2025-06-28.
- Balance-sheet instant: 2025-06-28.

### Checks performed

For every question input, a program matched the concept under `facts.us-gaap`, unit, exact accession, form 10-Q, end date, and start date (or absence of start for an instant fact). All 30 question-input selections matched, with no conflicting numeric values for a selection. Tags used by multiple questions were verified for each question.

Dates matter: AMD's fiscal first half starts in calendar 2024. Tesla's quarterly and year-to-date facts share the same end date. Filtering only on `fy` and `fp` cannot distinguish those durations.

The API reports monetary values in full USD, even when tables display millions. Questions requesting USD millions require division by 1,000,000. EPS uses `USD/shares` and must not receive that conversion.

Company-facts verification covers the standard concepts used here. It does not validate arbitrary segment dimensions, issuer-specific extensions, or the full original inline-XBRL context IDs. These questions do not require those capabilities.

The JSON checks confirmed 20 additions, ten of each type, five ordered questions per file, identical field names to the templates, and unique IDs and question text across all 60 records. This was source and dataset validation, not an agent or edgartools integration test. A completed answer key was not added.

## How each field was assigned

| Field | Basis |
| --- | --- |
| id | Continued XBRL-RET and XBRL-CMP numbering from 006 through 015; checked against all existing IDs. |
| question | Authored around verified facts, with exact company, accession, dates, output units, and rounding where needed. |
| type | XBRL Retrieval for extraction; XBRL Computation for calculations from tagged inputs. |
| answer | Descriptive symbolic placeholder. Multi-output tasks have a single result label representing their requested outputs. |
| scenario_id | XBRL-RETRIEVAL/COMPUTE-002 for Tesla and -003 for AMD; separates retrieval from computation. |
| workflow_step | Question order 1–5 within a file, not an assertion of dependency between questions. |
| total_steps | Five questions per scenario. |
| hops | Author-assigned: 1 for tagged lookup, 2 for input retrieval plus one calculation, 3 for a dependent derivation or multiple-duration selection plus calculation. Not a measured tool-call count. |
| xbrl_concepts | Exact us-gaap concept names confirmed in the SEC API for the selected accession and periods. |
| filing_type | 10-Q, verified in SEC metadata. |
| filing_period | Fiscal report period plus the exact input duration(s) or instant; may include year-to-date context. |
| answer_type | numeric_value for retrieval; calculated_value for computation, following the original vocabulary. |
| tool_required | Template's edgartools convention, with XBRL filtering and calculation capabilities specified. Runtime compatibility was not tested. |
| source | Direct SEC company-facts endpoint used to verify tagged facts. |
| reasoning | Author-written selection rules and formulas; no fabricated agent execution trace. |
| evidence | SEC filing URL, statement/row description, accession, filing date, dates, and unit. |

## Future evaluation

Keep answer placeholders and solution-oriented reasoning hidden from the evaluated agent. Define separately whether concept names and source URLs are visible hints. Resolve the placeholders with an independently reviewed answer key before scoring.

Reset state between independently scored scenarios. These are five-question groups; only explicitly described derivations have dependent calculations within a question. They are not represented as fully dependent long-horizon workflows.

