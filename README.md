# Trouve Sense — EnterpriseRAG-Bench submission (v2)

Self-evaluated results on the 500 core questions, scored with the official
EnterpriseRAG-Bench evaluator. These are our local figures, not an official rank.

## Result

| Metric | Score |
|---|---:|
| **Overall** | **88.41** |
| Correctness | 90.80 |
| Completeness | 92.52 |
| Recall | 93.07 |
| Invalid extra documents | 0.53 |

Questions scored: 500/500; skipped rows: 0.

### By question type

| Question type | N | Overall | Correctness | Completeness | Recall | Invalid extra docs |
|---|---:|---:|---:|---:|---:|---:|
| basic | 175 | 96.00 | 97.14 | 96.79 | 97.71 | 0.13 |
| semantic | 125 | 83.95 | 87.20 | 86.55 | 87.20 | 0.43 |
| intra_document_reasoning | 40 | 100.00 | 100.00 | 100.00 | 100.00 | 0.00 |
| project_related | 40 | 59.77 | 67.50 | 82.31 | 83.65 | 3.27 |
| constrained | 30 | 93.25 | 96.67 | 96.58 | 100.00 | 0.43 |
| conflicting_info | 20 | 90.33 | 95.00 | 92.83 | 92.50 | 0.25 |
| completeness | 20 | 67.01 | 70.00 | 80.02 | 77.34 | 1.10 |
| miscellaneous | 20 | 98.75 | 100.00 | 98.75 | 100.00 | 0.00 |
| high_level | 10 | 70.00 | 70.00 | 88.00 | 0.00 | 0.00 |
| info_not_found | 20 | 95.00 | 95.00 | 100.00 | 0.00 | 0.00 |

## Files

- `answers_trouve_sense.jsonl`: submission answers, one line per question with `question_id`, `answer`, `document_ids`.
- `results_trouve_sense.json`: evaluator output.
- `questions_updated_trouve_sense.jsonl`: evaluator-updated question set.
- `systems.yaml`: proposed `trouve_sense` system entry.
- `eval-provenance.json`: evaluator, question-set and answer hashes, judge settings.
- `MANIFEST.json`: SHA-256 of every file in this directory.

Frozen answers SHA-256:

`7bd5082ddf74112e0cd7c737a9182331d9353fed83d64a145a05ff9479d8fbbb`

## Evaluation

- Evaluator: upstream `metrics_based_eval` at `d36685e273713975ee20299bbf1ab64165575b3c`, unmodified (clean checkout).
- Judge: `gpt-5.4`, medium reasoning, reached through OpenRouter (provider OpenAI).
- Document correction and citation stripping: ON (evaluator defaults).
- One evaluator invocation over all 500 questions.
