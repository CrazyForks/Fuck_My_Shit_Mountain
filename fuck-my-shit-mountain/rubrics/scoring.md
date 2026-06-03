# Scoring Rubric

## Purpose

Provide an intuitive, at-a-glance assessment of codebase health across all audit dimensions. The score is a supplement to the detailed findings — it does not replace them.

## Dimension Scores

Each of the 6 dimensions is scored **0.0 – 10.0**:

| Dimension | Label |
|-----------|-------|
| Security | How resistant to attack |
| Stability | How reliable under failure |
| Performance | How efficient under load |
| Testing | How much confidence tests provide |
| Maintainability | How easy to change |
| Release | How ready to ship |

## Score Calculation

### Starting point

Each dimension starts at **10.0**.

### Deductions per finding

| Severity | Confirmed | Suspected |
|----------|-----------|-----------|
| Critical | –2.0 | –1.0 |
| High | –1.0 | –0.5 |
| Medium | –0.5 | –0.25 |
| Low | –0.2 | –0.1 |
| Info | 0.0 | 0.0 |

A finding only deducts from its **own dimension**. For example, a Critical security finding deducts –2.0 from Security, not from other dimensions.

### Cap & Rounding

- Minimum score per dimension: **0.0**
- Round to 1 decimal place.

### Overall Score

Average of all 6 dimension scores, rounded to 1 decimal place.

For focused audit modes (e.g., security-only), only report the relevant dimension score and note that other dimensions were not assessed.

## Grade Map

| Score | Grade | Label | Meaning |
|-------|-------|-------|---------|
| 9.0 – 10.0 | S | Clean | Production-ready. Minor nitpicks only. |
| 7.0 – 8.9 | A | Good | Solid. Some issues but low urgency. |
| 5.0 – 6.9 | B | Fair | Needs work. Medium risks present. |
| 3.0 – 4.9 | C | Poor | Significant risks. Should address before release. |
| 1.0 – 2.9 | D | Bad | Critical issues. Do not ship as-is. |
| 0.0 – 0.9 | F | Shit Mountain | High-severity issues across the board. Major rework needed. |

## Score Visualization

Render each dimension score as a 10-character ASCII bar:

```
Score bar: ████████░░
8.0 = ████████░░  (8 filled, 2 empty)
3.5 = ███░░░░░░░  (3.5 filled, 6.5 empty)
```

Filled blocks: `█` (use `\u2588`)
Empty blocks: `░` (use `\u2591`)

Number of filled blocks = floor(score). Remainder rounds up at ≥ 0.5.

### Example Dashboard

```
Security        ████████░░  8.0  A
Stability       ██████░░░░  6.0  B
Performance     █████████░  9.0  S
Testing         ████░░░░░░  4.0  C
Maintainability ███████░░░  7.0  A
Release         ██████░░░░  6.0  B
────────────────────────────────────
Overall         ███████░░░  6.7  B
```

## Rules

1. The score is derived from findings, not independent judgment. Do not adjust scores to match intuition.
2. If a dimension has no findings, score is 10.0 (Clean). This is correct — no evidence of problems means no deduction.
3. For suspected issues, use the halved deduction. This reflects lower confidence.
4. If the same issue is reported in both Confirmed and Suspected status, only count the Confirmed version.
5. Scores are relative to the audit scope. A security-only audit only assesses the Security dimension.
6. Include the score dashboard in the Executive Summary section of the report.
