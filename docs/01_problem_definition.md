# Problem Definition

## Project Type

Independent AI Systems Case Study

## Simulated Business Need

A simulated ecommerce retailer receives customer support messages that need to be classified into approved categories before they can eventually be routed to the correct support team.

## Approved Categories

1. Order Status
2. Return or Refund
3. Damaged or Incorrect Item
4. Cancellation
5. Payment or Billing
6. Account Access
7. Product Question
8. Other

## Reliability Challenges

The classifier needed to handle more than obvious single issue messages. The controlled test set deliberately included multiple issues, sarcasm, negation, vague requests, irrelevant background information, partial uncertainty, prompt injection inside customer text, and unclear category boundaries.

## Design Objective

The objective was not simply to make a longer prompt. The case study asked which responsibilities belonged to the language model, which belonged to deterministic rules, how uncertainty should be represented, and how changes should be evaluated through controlled regression testing.

## Evidence Boundary

This was a simulated use case using synthetic messages. No real retailer, customer data, production traffic, or deployed routing system was involved.
