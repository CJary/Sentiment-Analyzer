# Apple SEC benchmark | apple-run-001

**Result: 5 of 5 answers correct.** The Codex CLI agent completed the full set in one turn. Its event log shows it opening Apple’s SEC filing with its web tool.

| Run detail | Recorded value |
|---|---|
| Agent | Codex CLI with web retrieval |
| Model | `gpt-6-astra` |
| Reasoning effort | `low` |
| Settings source | Saved Codex session, `turn_context` for session `01a1d6dd-9d79-7082-a7a5-6e7aa887c2c2` |
| Dataset | [Apple FY2025 Q2 SEC computation](../../../../../Dataset/sec/compute/sec_compute_aapl_10q.json), SEC-CMP-006 through SEC-CMP-010 |
| Elapsed wall time | **27.625 seconds** for the full CLI run |
| Set token usage | **103,320 total** (102,657 input and 663 output) |
| Cached input | 85,632 tokens, included in input |
| Reasoning summary | Unavailable. No reasoning summary was emitted in the saved events. |
| Required retrieval tool | The dataset specifies `sec-edgar-toolkit`. This run used Codex web retrieval, so it serves as a baseline. |

## Verified results

The reviewer checked the source figures in [Apple’s FY2025 Q2 Form 10-Q](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm) and independently recalculated each answer.

| Question | Agent answer | Verification |
|---|---:|---|
| SEC-CMP-006 · Year-over-year quarterly sales growth | 5.08% | (95,359 − 90,753) ÷ 90,753 × 100 |
| SEC-CMP-007 · Quarterly operating margin | 31.03% | 29,589 ÷ 95,359 × 100 |
| SEC-CMP-008 · Current ratio | 0.8209:1 | 118,674 ÷ 144,571 |
| SEC-CMP-009 · Services share of quarterly sales | 27.94% | 26,645 ÷ 95,359 × 100 |
| SEC-CMP-010 · Derived Q1 sales and sequential growth | USD 124,300 million and −23.28% | Q1 = 219,659 − 95,359. Growth = (95,359 − 124,300) ÷ 124,300 × 100. |

The [original agent output and web tool events](events.jsonl) preserve the response, cited filing sections, and reported usage. The [submitted prompt](prompt.txt) contains all five questions. The [timing file](timing-and-stderr.txt) records the elapsed time.
