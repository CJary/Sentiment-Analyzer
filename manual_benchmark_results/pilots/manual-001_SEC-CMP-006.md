# Manual Benchmark Result — SEC-CMP-006

> **Pilot only.** This run covered 1 of 5 questions. Set token usage and the original reasoning display were not captured. See [the full-set procedure](../sets/apple-fy2025-q2-sec-compute/procedure.md) for the next run.

Run ID: `manual-001`  
Report prepared: November 3, 2026  
Run date: Not recorded

## Setup

| Field | Value |
|---|---|
| Platform | ChatGPT, manual execution |
| Model / setting | GPT-6, medium thinking (user-reported; exact model version not captured) |
| Benchmark | SEC-CMP-006 — Apple quarterly net sales growth |
| Dataset | [Apple SEC computation](../../Dataset/sec/compute/sec_compute_aapl_10q.json), first question |
| Test scope | Financial question-answering baseline |
| Input | Benchmark prompt supplied in this chat; exact submitted request not separately archived |

## Question

> Using Apple's FY2025 Q2 10-Q, calculate total net sales growth from the three months ended March 30, 2024 to the three months ended March 29, 2025. Return a percentage rounded to two decimal places.

## Recorded outcomes

| Outcome | Result |
|---|---|
| Final answer | **5.08% year-over-year growth** |
| Calculation explanation | `(95,359 − 90,753) / 90,753 × 100 = 5.08%` |
| Runtime | **12.32 seconds**, manually timed by the user |
| Token usage | **N/A** — per-request usage was not available from the interface; no estimate substituted |

The model reported total net sales of **USD 90,753 million** for the three months ended March 30, 2024 and **USD 95,359 million** for the three months ended March 29, 2025. It reported an increase of **USD 4,606 million**.

The explanation above is the model's visible calculation summary, not private internal reasoning. Runtime represents user-observed elapsed response time, not isolated model computation time.

## Evidence and evaluation

The model cited [Apple's FY2025 Q2 Form 10-Q](https://www.sec.gov/Archives/edgar/data/320193/000032019325000057/aapl-20250329.htm), Part I, Item 1, Condensed Consolidated Statements of Operations, “Total net sales,” three-month columns. It stated that it accessed the filing successfully and encountered no source-access limitations. This is a model-reported claim; no retrieval trace was supplied.

| Check | Assessment |
|---|---|
| Arithmetic and rounding | Pass: independently recalculated from the supplied figures; result rounds to 5.08% |
| Periods and units in response | Match the requested three-month periods; inputs reported in USD millions |
| Filing values / numeric ground truth | Pending independent verification against the original filing |
| Required tool | Dataset specifies `sec-edgar-toolkit`; its use was not demonstrated |
| Overall status | Manual pilot recorded; full benchmark compliance not established |

## Review takeaway

This run demonstrates a practical record format for the answer, calculation explanation, and manual runtime. Token usage remains unavailable. Before scaling, verify the filing values, archive the exact prompt and model settings, and choose a runner that exposes token usage and tool traces. One run does not establish broader accuracy or runtime consistency.
