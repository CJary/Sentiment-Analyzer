# Benchmark datasets

Question sets are grouped by source method (SEC filing text or XBRL facts), then by task (computation or retrieval). Each JSON file is one five-question set. Run records live separately in [Manual benchmark results](../manual_benchmark_results/README.md).

## SEC compute

| Dataset | Question IDs |
|---|---|
| [sec_compute_aapl_10q](sec/compute/sec_compute_aapl_10q.json) | SEC-CMP-006 through SEC-CMP-010 |
| [sec_compute_amzn](sec/compute/sec_compute_amzn.json) | SEC-CMP-001 through SEC-CMP-005 |
| [sec_compute_nvda_8k](sec/compute/sec_compute_nvda_8k.json) | SEC-CMP-011 through SEC-CMP-015 |

## SEC retrieval

| Dataset | Question IDs |
|---|---|
| [sec_retrieval_aapl_10q](sec/retrieval/sec_retrieval_aapl_10q.json) | SEC-RET-006 through SEC-RET-010 |
| [sec_retrieval_msft](sec/retrieval/sec_retrieval_msft.json) | SEC-RET-001 through SEC-RET-005 |
| [sec_retrieval_nvda_8k](sec/retrieval/sec_retrieval_nvda_8k.json) | SEC-RET-011 through SEC-RET-015 |

## XBRL compute

| Dataset | Question IDs |
|---|---|
| [xbrl_compute_amd_10q](xbrl/compute/xbrl_compute_amd_10q.json) | XBRL-CMP-011 through XBRL-CMP-015 |
| [xbrl_compute_cost_10q](xbrl/compute/xbrl_compute_cost_10q.json) | XBRL-CMP-031 through XBRL-CMP-035 |
| [xbrl_compute_ko_10q](xbrl/compute/xbrl_compute_ko_10q.json) | XBRL-CMP-016 through XBRL-CMP-020 |
| [xbrl_compute_meta](xbrl/compute/xbrl_compute_meta.json) | XBRL-CMP-001 through XBRL-CMP-005 |
| [xbrl_compute_pep_10q](xbrl/compute/xbrl_compute_pep_10q.json) | XBRL-CMP-021 through XBRL-CMP-025 |
| [xbrl_compute_tsla_10q](xbrl/compute/xbrl_compute_tsla_10q.json) | XBRL-CMP-006 through XBRL-CMP-010 |
| [xbrl_compute_wmt_10q](xbrl/compute/xbrl_compute_wmt_10q.json) | XBRL-CMP-026 through XBRL-CMP-030 |

## XBRL retrieval

| Dataset | Question IDs |
|---|---|
| [xbrl_retrieval_amd_10q](xbrl/retrieval/xbrl_retrieval_amd_10q.json) | XBRL-RET-011 through XBRL-RET-015 |
| [xbrl_retrieval_cost_10q](xbrl/retrieval/xbrl_retrieval_cost_10q.json) | XBRL-RET-031 through XBRL-RET-035 |
| [xbrl_retrieval_jnj](xbrl/retrieval/xbrl_retrieval_jnj.json) | XBRL-RET-001 through XBRL-RET-005 |
| [xbrl_retrieval_ko_10q](xbrl/retrieval/xbrl_retrieval_ko_10q.json) | XBRL-RET-016 through XBRL-RET-020 |
| [xbrl_retrieval_pep_10q](xbrl/retrieval/xbrl_retrieval_pep_10q.json) | XBRL-RET-021 through XBRL-RET-025 |
| [xbrl_retrieval_tsla_10q](xbrl/retrieval/xbrl_retrieval_tsla_10q.json) | XBRL-RET-006 through XBRL-RET-010 |
| [xbrl_retrieval_wmt_10q](xbrl/retrieval/xbrl_retrieval_wmt_10q.json) | XBRL-RET-026 through XBRL-RET-030 |

## Adding a set

Use the existing naming pattern `<source>_<task>_<ticker>[_<filing>].json`. Keep each set’s five questions and IDs stable, then add a row to this index. Keep grading fields such as `answer`, `reasoning`, and `evidence` out of the agent prompt.

## Dataset notes

- [ADDITIONS_10Q_8K](notes/ADDITIONS_10Q_8K.md)
- [ADDITIONS_XBRL_2026_09_18](notes/ADDITIONS_XBRL_2026_09_18.md)
- [ADDITIONS_XBRL_2026_09_22](notes/ADDITIONS_XBRL_2026_09_22.md)
