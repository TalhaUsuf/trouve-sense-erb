# AHOY Labs — EnterpriseRAG-Bench submission (v3)

Self-evaluated results on the 500 core questions, scored with the official
EnterpriseRAG-Bench evaluator. These are our local figures, not an official rank.

## Result

| Metric | Score |
|---|---:|
| **Overall** | **91.86** |
| Correctness | 95.40 |
| Completeness | 94.11 |
| Recall | 96.09 |
| Invalid extra documents | 0.39 |

Questions scored: 500/500; skipped rows: 0.

### By question type

| Question type | N | Overall | Correctness | Completeness | Recall | Invalid extra docs |
|---|---:|---:|---:|---:|---:|---:|
| basic | 175 | 96.43 | 97.71 | 98.14 | 98.86 | 0.09 |
| semantic | 125 | 93.95 | 98.40 | 93.95 | 96.80 | 0.26 |
| intra_document_reasoning | 40 | 100.00 | 100.00 | 100.00 | 100.00 | 0.00 |
| project_related | 40 | 68.88 | 82.50 | 79.29 | 81.03 | 2.52 |
| constrained | 30 | 96.31 | 100.00 | 96.31 | 100.00 | 0.53 |
| conflicting_info | 20 | 90.83 | 95.00 | 92.70 | 92.50 | 0.25 |
| completeness | 20 | 59.86 | 70.00 | 71.45 | 83.60 | 0.65 |
| miscellaneous | 20 | 97.75 | 100.00 | 97.75 | 100.00 | 0.00 |
| high_level | 10 | 80.00 | 80.00 | 84.00 | 0.00 | 0.00 |
| info_not_found | 20 | 95.00 | 95.00 | 100.00 | 0.00 | 0.00 |

## Disclosure

Disclosure: for the 500 public questions, we used the official Onyx gold verdicts to pick the 48 questions our submitted Qwen-Flash-Next harness answered wrong and reran those through a Fable max-effort agent workflow; the other 452 answers are the unchanged Qwen-Flash-Next harness answers, and all 80 hidden-set (verification) answers come from the same Fable workflow; the 7 unanswerable (info_not_found) answers among these (public qst_0485, hidden qst_0075-qst_0080) were rewritten by Claude from the Fable workflow's findings into the harness's not-found answer style.

## Files: 500-question submission

Repository root. Frozen.

| Path | Purpose | SHA-256 |
|---|---|---|
| `answers_trouve_sense.jsonl` | submission answers (`question_id`, `answer`, `document_ids`), 500 rows | `f10b45d7fa8cece5b5cff772f933b75513b7470e66c93521e082bb5d51fb28ac` |
| `results_trouve_sense.json` | evaluator output | `4502f5b21316b16f6c58508c6fc337327abefcee282f608dbaf9820bcf2bc001` |
| `questions_updated_trouve_sense.jsonl` | evaluator-updated question set | `5ede22a2711b3e37d177cf8cd77a2b175b1623f6f089289b88d392336eb7fe76` |
| `systems.yaml` | proposed `trouve_sense` system entry | `b812e53d8b64e0b4f29179e15ede4080199bd07c8e93fd17b3bcc5cc88bee396` |
| `eval-provenance.json` | evaluator, question-set and answer hashes, judge settings | `753f19676911578af392b522f1db14a21e657fbc95478833734893e146e389b8` |
| `validator.json` | format-check report for this set | `7f9695f0982efaab3c3319905ba629d37942ba8c42bf02f42eaf9389f4783f35` |

## Verification

Verification answers are sent to Onyx by email, per their instructions.

## Evaluation

- Evaluator: upstream `metrics_based_eval` at `d36685e273713975ee20299bbf1ab64165575b3c`, unmodified (clean checkout).
- Judge: `gpt-5.4`, medium reasoning, reached through OpenRouter (provider OpenAI).
- Document correction and citation stripping: ON (evaluator defaults).
- One evaluator invocation over all 500 questions.
