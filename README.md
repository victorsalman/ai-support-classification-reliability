# AI Support Classification Reliability

**Independent AI Systems Case Study**

AI Support Classification Reliability is an independent AI systems case study exploring how an ecommerce support classifier can be made more reliable through clearer business taxonomy, structured outputs, uncertainty preservation, adversarial testing, and controlled regression testing. The project focuses on prompt engineering and workflow evaluation rather than software deployment. All test messages were synthetic, and all model outputs were generated in controlled GPT 5.6 Sol conversational runs rather than independent API or production benchmarks.

## The Business Problem

A simulated online retailer needed to classify support messages into eight approved categories:

1. Order Status
2. Return or Refund
3. Damaged or Incorrect Item
4. Cancellation
5. Payment or Billing
6. Account Access
7. Product Question
8. Other

Simple messages were easy to classify. The difficult cases involved multiple issues, sarcasm, negation, vague requests, prompt injection, partial uncertainty, and unclear taxonomy boundaries.

## What Changed

The baseline structure returned `detected_categories` plus a message level `review_required` flag. That could indicate that a message needed review, but it could not preserve which specific issue was uncertain.

The later structure separated:

`confirmed_categories`

from

`uncertain_categories`

This preserved partial uncertainty instead of flattening the entire message into one review state.

Exact rules such as schema validation, approved category enforcement, duplicate prevention, review triggers, and routing priority were kept conceptually outside the language model.

## Testing Progression

**Baseline controlled dry run**

24 synthetic messages were evaluated once. The expected category set matched on 14 of 24 messages.

**Version 2.1 controlled test**

24 messages were run three times each, producing 72 controlled outputs. 68 of 72 matched the frozen expectations. Three boundary failure families remained.

**Version 2.2 controlled regression test**

The original 24 cases were preserved and 14 boundary cases were added. The 38 messages were run three times each, producing 114 controlled outputs. All 114 matched the frozen expected results, and all 38 messages were consistent across the three controlled runs.

These results describe this controlled conversational case study only. They are not production accuracy claims and were not independent API benchmarks.

## Key Lessons

1. Taxonomy is part of system design.
2. Uncertainty should be preserved rather than hidden.
3. Context is not automatically evidence of an issue.
4. Customer supplied instructions should be treated as untrusted content.
5. Exact rules belong outside probabilistic classification when they can be calculated deterministically.
6. Testing should drive prompt changes.
7. Further prompt complexity should stop when the evidence no longer justifies it.

## Architecture

![Workflow architecture](assets/workflow_architecture.png)

The language model handles semantic interpretation. Recommended deterministic software responsibilities include schema validation, approved category enforcement, duplicate prevention, review triggers, routing priorities, and exact business rules.

## Repository Navigation

1. [Problem definition](docs/01_problem_definition.md)
2. [Taxonomy](docs/02_taxonomy.md)
3. [Failure analysis](docs/03_failure_analysis.md)
4. [Architecture](docs/04_architecture.md)
5. [Safety and reliability](docs/05_safety_and_reliability.md)
6. [Limitations](docs/06_limitations.md)
7. [Baseline prompt](prompts/01_baseline_prompt.md)
8. [Version 1 prompt](prompts/02_version_1_prompt.md)
9. [Version 2.1 prompt](prompts/03_version_2_1_prompt.md)
10. [Version 2.2 final case study prompt](prompts/04_version_2_2_final_prompt.md)
11. [Test cases](data/test_cases.json)
12. [Frozen expected results](data/gold_expected_results.json)
13. [Baseline controlled results](data/baseline_controlled_results.json)
14. [Version 1 controlled results](data/version_1_controlled_results.json)
15. [Version 2.1 controlled results](data/version_2_1_controlled_results.json)
16. [Version 2.2 controlled results](data/version_2_2_controlled_results.json)

## Skills Demonstrated

Prompt engineering, AI workflow evaluation, structured outputs, regression testing, failure analysis, adversarial testing, uncertainty preservation, taxonomy design, hallucination reduction, and human review design.

This project does not claim professional software engineering, production deployment, machine learning engineering, or independent security validation.
