# Additional 10-Q and 8-K benchmark scenarios

Added 20 questions: 10 retrieval and 10 computation, in four five-question scenarios.

| File | Company | Filing | Questions |
| --- | --- | --- | --- |
| sec_retrieval_aapl_10q.json | Apple | FY2025 Q2 10-Q | 5 retrieval |
| sec_compute_aapl_10q.json | Apple | FY2025 Q2 10-Q | 5 computation |
| sec_retrieval_nvda_8k.json | NVIDIA | May 28, 2025 8-K, Exhibit 99.1 | 5 retrieval |
| sec_compute_nvda_8k.json | NVIDIA | May 28, 2025 8-K, Exhibit 99.1 | 5 computation |

## Source verification

Reviewed the following SEC-hosted documents on 2026-09-15. Every requested fact or calculation input was located in these documents. This verifies question answerability; it is not an agent execution test or a completed answer key.

- [Apple 10-Q, accession 0000320193-25-000057](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm): statements of operations and balance sheets; Note 2 revenue table; MD&A Services discussion. The filing includes both quarterly and six-month figures, and prior-year quarterly comparatives.
- [NVIDIA 8-K, accession 0001045810-25-000115](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000115/nvda-20250528.htm): Item 2.02 links the earnings release as Exhibit 99.1.
- [NVIDIA Exhibit 99.1](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000115/q1fy26pr.htm): GAAP/non-GAAP summary tables, H20 discussion, dividend announcement, outlook, cash flow statement, and free cash flow definition. The exhibit is furnished with the 8-K. Its financial quarter is FY2026 Q1 although the report date is in calendar 2025.

Each question's `source` points directly to its SEC document and `evidence` identifies the relevant table or passage.

## Format and evaluation notes

- Preserves the original 16-field JSON format and placeholder answers. Original files are unchanged.
- New question IDs are SEC-RET-006 through SEC-RET-015 and SEC-CMP-006 through SEC-CMP-015. Scenario IDs use suffixes 003 and 004.
- All new records use SEC Retrieval or SEC Computation. Empty `xbrl_concepts` arrays are intentional: these questions target document text/table extraction and do not assert unverified XBRL tags. In particular, financial information in an 8-K exhibit should not be assumed available through company-facts XBRL.
- `tool_required` describes the expected capability using the template's naming convention; availability of that tool has not been tested.
- For this batch, `hops` counts a direct lookup as 1, section/exhibit navigation plus extraction as 2, and exhibit-based computation or a dependent calculation as 3. It is an intended task-depth label, not a measured tool-call count.
- Steps are ordered scenario questions, not necessarily dependent tasks. These files are not presented as a completed long-horizon benchmark.
- Calculation questions specify periods, units, formulas, and rounding. Keep full precision until final rounding.
- If retrieval and computation scenarios are evaluated separately, reset agent state between them to prevent earlier answers from leaking into subsequent runs.
- A future runner must hide `answer` and solution-oriented `reasoning` from the evaluated agent and resolve placeholders through a separately verified answer key.

