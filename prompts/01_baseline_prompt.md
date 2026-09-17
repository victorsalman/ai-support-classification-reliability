# Baseline Prompt

## Purpose

Establish a plausible minimal starting point for controlled classification testing.

## Problem This Version Addressed

The baseline gave the model the approved categories, a structured output shape, and a basic uncertainty path, but little guidance about multiple issues, negation, adversarial customer text, or taxonomy boundaries.

## What Remained Outside the Model

No production routing or deterministic validation was implemented. This prompt was used only as a controlled case study baseline.

## Exact Prompt

```text
Classify the following customer support message.

Choose one or more categories from:

Order Status

Return or Refund

Damaged or Incorrect Item

Cancellation

Payment or Billing

Account Access

Product Question

Other

Return JSON in this format:

{
  "detected_categories": [],
  "review_required": false
}

If you cannot determine the correct category, set review_required to true.

Customer message:

{{customer_message}}
```
