# Failure Analysis

## Baseline Weaknesses

The minimal baseline handled straightforward messages but missed important failure boundaries.

Observed controlled dry run problems included:

1. Missing secondary issues in multi issue messages.
2. Treating sarcasm as an unrelated complaint.
3. Forcing vague messages into a category.
4. Following instructions embedded inside customer text.
5. Treating negated concepts as active requests.
6. Losing the distinction between confirmed and uncertain issues.

## Version 1 Improvement and Hidden Information Loss

Version 1 added stronger classification rules and a human review path. It improved the controlled dry run substantially, but the schema still used `detected_categories` plus one `review_required` flag.

That structure could not preserve which specific category was uncertain when a message contained both clear and uncertain issues.

## Version 2.1 Remaining Failures

Version 2.1 separated `confirmed_categories` from `uncertain_categories`. In 72 controlled outputs, 68 matched the frozen expectations.

Three failure families remained.

### Taxonomy Ambiguity

`Do you sell gift cards?` alternated between Product Question and Other because the business taxonomy had not explicitly defined that boundary.

### Context Mistaken for Evidence

`I ordered something last week and now there's another thing I need help with.` was once interpreted as uncertain Order Status even though no status issue was actually expressed.

### Vague Dissatisfaction Mistaken for Item Failure

`Why did you idiots send this?` was once interpreted as uncertain Damaged or Incorrect Item even though no damage or mismatch was stated.

## Root Cause

The remaining problems were not evidence that the full architecture needed another model stage. They showed that category boundaries and evidence thresholds were still underspecified.

## Version 2.2 Correction

Only the smallest supported corrections were made:

1. Strengthen the evidence threshold.
2. Tighten the meaning of uncertain classification.
3. Clarify Product Question boundaries.
4. Clarify Damaged or Incorrect Item boundaries.

No second reviewer model was added. No confidence percentage was invented. No crude keyword patch was added.

The expanded controlled regression set then produced 114 of 114 outputs matching the frozen expectations.

This is a controlled case study result, not a production accuracy claim.
