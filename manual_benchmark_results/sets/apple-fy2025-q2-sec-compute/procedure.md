# Apple FY2025 Q2 benchmark procedure

Run all five questions (SEC-CMP-006 through SEC-CMP-010) in order in one fresh session. The [ready-to-run prompt](prompt.txt) includes the questions and filing link. Record this as a Codex baseline using the selected model and reasoning effort.

Source dataset: [Apple FY2025 Q2 SEC computation](../../../Dataset/sec/compute/sec_compute_aapl_10q.json).

## Capture one full run

The installed Codex CLI reports that it is signed in with ChatGPT. Open Terminal in this set folder, alongside this procedure and `prompt.txt`, then run the following command. Pick a new run ID for every attempt. The command saves a copy of the prompt, the original events emitted by the CLI, and the elapsed wall time.

```sh
run_dir=runs/apple-run-002
mkdir "$run_dir" &&
cp prompt.txt "$run_dir/prompt.txt" &&
{ time env -u OPENAI_API_KEY -u CODEX_API_KEY codex exec --model gpt-6-astra -c model_reasoning_effort=low --json --skip-git-repo-check --sandbox read-only - < "$run_dir/prompt.txt" > "$run_dir/events.jsonl"; } 2> "$run_dir/timing-and-stderr.txt"
```

Confirm that the final answer contains all five IDs. Review the terminal timing file for elapsed time and errors. Save the requested model and reasoning effort with the run. The command pins `gpt-6-astra` and `low` to reproduce apple-run-001. Verify the recorded settings in the saved session’s `turn_context` by matching its session ID to `thread.started.thread_id` in the event log. Review the event log for the final answer, source lookups, and any reasoning summary. Save emitted reasoning or tool events verbatim with their event labels. Share only the relevant excerpts from logs if unrelated local context appears.

For set token usage, read the `usage` object on the `turn.completed` event. Save input and output counts separately. Preserve cached input and reasoning output as breakdowns when available. For this single-turn protocol, the completed turn is the set. If the event is missing, record usage as unavailable and the run as incomplete. See [Codex JSON event documentation](https://learn.chatgpt.com/docs/non-interactive-mode).

## Report the result

Record the run ID, model, reasoning effort, source access method, all five answers, correct answers out of five after independent filing verification, elapsed seconds, input and output tokens for the set, and links to the captured evidence. Record whether the dataset's required `sec-edgar-toolkit` was actually used. Label other retrieval methods as a baseline.

Ask the lead whether the verbatim reasoning display and tool events meet the evidence requirement. The original hidden reasoning text is unavailable from OpenAI. If that exact requirement is mandatory, agree on a different model and runner that explicitly exposes a generated reasoning trace before collecting benchmark results. See [OpenAI reasoning documentation](https://developers.openai.com/api/docs/guides/reasoning#reasoning-summaries).

See [apple-run-001](runs/apple-run-001/report.md) for a completed example.
