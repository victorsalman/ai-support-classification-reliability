# Architecture

## What Was Actually Tested

GPT 5.6 Sol was used inside a controlled conversation to classify synthetic customer messages using frozen prompt versions.

The final tested output structure was:

```json
{
  "confirmed_categories": [],
  "uncertain_categories": []
}
```

The controlled cases tested semantic classification behavior including multiple issues, negation, sarcasm, ambiguous messages, partial uncertainty, and prompt injection inside customer text.

## What Was Recommended Conceptually

The following exact responsibilities were recommended for deterministic software rather than the language model:

1. Approved category enum validation.
2. JSON schema validation.
3. Duplicate category prevention.
4. Prevention of the same category appearing in both arrays.
5. Human review triggers.
6. Routing priority when multiple categories exist.
7. Exact business rules that can be calculated deterministically.

These components were architecture recommendations. Production code implementing them was not built in this case study.

## What Would Still Need to Be Built

A real implementation would still require:

1. Application integration.
2. API execution harness.
3. Schema validation code.
4. Routing logic.
5. Human review workflow.
6. Logging and monitoring.
7. Privacy and data handling controls.
8. Cost and latency measurement.
9. Production evaluation against representative real customer traffic.

## Responsibility Split

The language model is best used here for semantic interpretation of natural language.

Deterministic software is better suited to exact validation and routing rules.

Human review remains appropriate when uncertainty cannot be safely resolved automatically.
