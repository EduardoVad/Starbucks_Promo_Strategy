# Starbucks Promotional Campaign — Customer Targeting Strategy

## Overview
Analysis of a randomized promotion experiment to identify which customers 
should receive a $10 product promotion costing $0.15 per send. 
The goal was to maximize Incremental Response Rate (IRR) and 
Net Incremental Revenue (NIR) by targeting only the most responsive customers.

## Business Context
Sending the promotion to everyone is unprofitable. A baseline analysis showed:
- **Baseline IRR:** 0.0095 — less than 1 additional purchase per 100 customers
- **Baseline NIR:** -$2,334.60 — a net loss from mass promotion

The challenge was identifying the right customers to flip NIR positive.

## Dataset
- **Training.csv** — 84,534 customers from a randomized experiment
- **Test.csv** — 41,650 customers used for final evaluation
- Features: V1–V7 (customer characteristics) + Promotion + purchase

## Approach
1. Calculated baseline IRR and NIR to establish experiment-level results
2. Analyzed IRR by segment across all features (V1–V7) to identify 
   which customer characteristics drive the highest incremental response
3. Built a rule-based targeting strategy based on the strongest segments
4. Evaluated strategy on held-out test set

## Key Finding — Feature IRR Analysis
| Feature | Best Segment | IRR | Worst Segment | IRR |
|---|---|---|---|---|
| V4 | V4 = 2 | 0.0141 | V4 = 1 | -0.0003 |
| V5 | V5 = 3 | 0.0143 | V5 = 2 | 0.0025 |
| V1 | V1 = 2 | 0.0124 | V1 = 3 | 0.0056 |

V4 and V5 emerged as the strongest targeting features with the widest 
spread between best and worst segments.

## Targeting Strategy
**Promote customers where: V4 = 2 AND (V5 = 3 OR V5 = 1)**

## Results on Test Set
| Metric | Baseline | Targeted |
|---|---|---|
| Customers | 41,650 (100%) | 8,016 (19.2%) |
| IRR | 0.0095 | 0.0228 |
| NIR | -$2,334.60 | +$298.10 |

By targeting 19% of customers the promotion went from a **$2,334 loss 
to a $298 gain** — a $2,632 swing in net incremental revenue.

## Tools
Python · Pandas · NumPy · VS Code · GitHub

## Author
Eduardo Vadillo Polo
