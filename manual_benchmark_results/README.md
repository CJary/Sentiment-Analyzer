# Manual benchmark results

Start with the [dataset index](../Dataset/README.md) to choose a five-question set.

| Set | Setup | Completed runs |
|---|---|---|
| Apple FY2025 Q2 SEC computation | [Prompt](sets/apple-fy2025-q2-sec-compute/prompt.txt) · [Procedure](sets/apple-fy2025-q2-sec-compute/procedure.md) | [apple-run-001](sets/apple-fy2025-q2-sec-compute/runs/apple-run-001/report.md) |

The [one-question Apple pilot](pilots/manual-001_SEC-CMP-006.md) is kept separately.

## Adding a run

1. For a new set, create a folder under `sets/` named for the company, filing period, and task. Add the reusable `prompt.txt` and `procedure.md`, and link to the source dataset.
2. For each attempt, create a new folder under that set’s `runs/`. Save the exact submitted prompt, original agent output and tool events, and timing data together.
3. Add a `report.md` with the agent and tools used, model and reasoning effort, all five answers and their verification, elapsed time, set token usage, and any reasoning summary the runner emitted. Record missing measurements as unavailable.
4. Link the report from this index.
