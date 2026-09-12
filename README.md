# Trouve Sense — EnterpriseRAG-Bench submission

<!-- REVIEW: one or two sentences of product framing, mirroring Skyller's.
     Replace with the wording you want public. -->
Trouve Sense is an enterprise document-intelligence system over
MinerU-parsed, visually-enriched document corpora. Document retrieval and
grounded answering, evaluated by EnterpriseRAG-Bench, is one of its modules.

## Result

This submission contains 500/500 answers and was evaluated locally with the
official EnterpriseRAG-Bench evaluator at commit
`d36685e273713975ee20299bbf1ab64165575b3c`, using GPT-5.4 with medium reasoning
and the standard gold-question correction flow.

| Metric | Score |
|---|---:|
| **Overall** | **75.17** |
| Correctness | 79.80 |
| Completeness | 81.78 |
| Recall | 82.15 |
| Invalid extra documents | 1.05 |

The included leaderboard snapshot projects Trouve Sense in fourth place. That is
a local projection, not an official rank, until Onyx verifies the run and
updates the leaderboard.

## Public artifacts

- `answers_trouve_sense.jsonl`: exact submission format, with only
  `question_id`, `answer`, and `document_ids` per line.
- `results_trouve_sense.json`: official evaluator output.
- `questions_updated_trouve_sense.jsonl`: complete evaluator-updated question
  set (14 questions corrected by the three-judge consensus flow).
- `systems.yaml`: proposed upstream `trouve_sense` system entry.

Frozen answer SHA-256:

`069a83e77ccb76705aaac7f38b057f19cf82b67deefa5d1d509e3b2f05a3ee04`

## Evaluation environment

The evaluator was run unmodified. The only local change to the upstream
repository at that commit is an additive branch in `src/llm/factory.py`
registering an extra provider; it is not reachable under `LLM_PROVIDER=openai`
and was not used for this run. `metrics_based_eval.py`, `eval_utils.py`,
`openai_llm.py` and `questions.jsonl` are unmodified at
`d36685e273713975ee20299bbf1ab64165575b3c`.

Citation stripping and the document-correction flow were both left ON, at the
evaluator's defaults. All 500 questions are scored; `skipped_rows` is 0.

The judge was reached through an OpenAI-compatible gateway, which resolved
`gpt-5.4` to snapshot `gpt-5.4-20260305` at medium reasoning effort. Exact
snapshot and provider-endpoint identity with Onyx's own evaluation runs is
therefore not something we can assert.

## Closed-source reproducibility

Trouve Sense is closed source. Onyx can verify it through the same live
retrieval and answering pipeline, benchmark corpus, and benchmark agent used for
the submitted run.

<!-- REVIEW: confirm before publishing. Nothing below is live yet. -->
Dedicated access will be prepared and shared with Onyx through a private
channel. Verification uses the literal benchmark question, one new conversation
per question, and no gold answer, expected document id, category, or prior
conversation context.

The harness runs a local model at non-zero temperature, so a live re-run does not
reproduce a submitted answer verbatim. We measured this rather than assert it: over
10 submitted questions re-asked through the verification endpoint, 8 cited exactly
the same documents as the frozen file and 2 did not. The frozen
`answers_trouve_sense.jsonl` is the submission; live access is how Onyx confirms it
came from a real system.

No credential, internal company identifier, private endpoint, or local path is
included in these public artifacts.
