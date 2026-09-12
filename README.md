# Trouve Sense — EnterpriseRAG-Bench submission

<!-- REVIEW: one or two sentences of product framing, mirroring Skyller's.
     Replace with the wording you want public. -->
'Trouve Sense' is a research project focused on intelligent decision making over semantically noisy large scale corpus.
`EnterpriseRAG-Bench` is by far the only relevant benchmark to test the capabilities of harness.

'Trouve Sense' uses all local components including the Data Layer, Retrieval Layer, Agent Harness Layer and the Local AI services.

## Result

This submission contains 500/500 answers and was evaluated locally with the
official EnterpriseRAG-Bench evaluator using GPT-5.4 wwith medium reasoning.

As per our evals following are the results (we ran eval multiple times to confirm):

| Metric | Score |
|---|---:|
| **Overall** | **75.17** |
| Correctness | 79.80 |
| Completeness | 81.78 |
| Recall | 82.15 |
| Invalid extra documents | 1.05 |


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
repository is registering an extra provider i.e. openrouter; ( judge model and reasoning effort kept same)
`metrics_based_eval.py`, `eval_utils.py`,
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

**NOTE:**
**The harness runs a local model at non-zero temperature, so a live re-run does not
reproduce a submitted answer verbatim.**

The credentials and sandbox endpoint will be provided via emAil.
