# Scoring Rubric

## Principle

Scores are **judgment-based, not formula-based.** The AI evaluates each dimension holistically based on the evidence collected, then assigns a score. There is no mechanical "Critical = -2.0" deduction — that produces inflated scores and false precision.

## Scale

Each dimension is scored **0.0 – 10.0**:

- **10.0** = Maximum shit mountain. This dimension is a disaster. Unacceptable risk. Complete overhaul needed.
- **0.0** = Completely healthy. No issues found. Production-ready.
- The score reflects **engineering risk and maintenance cost**, not code style preference.

## Dimensions

| Dimension | What It Measures | Mapped From Modes |
|-----------|-----------------|-------------------|
| Security | How resistant to attack. Auth, injection, secrets, dependency risk. | security, type-safety |
| Stability | How reliable under failure. Panic paths, error handling, retry, timeout, state consistency, fallback quality. | stability, fallback |
| Performance | How efficient under realistic load. Hot paths, memory, I/O, contention. | performance, dependency-weight |
| Testing | How much real confidence tests provide. Coverage quality, test types, authenticity. | testing, testing-authenticity |
| Maintainability | How easy to change. Complexity, coupling, duplication, naming, state management, API design. | maintainability, frontend-state, backend-api |
| Design | How well it follows engineering principles. SRP, DRY, KISS, fail-fast, type safety. | (cross-cutting) |
| Release | How ready to ship. CI/CD, versioning, upgrade, rollback, dependency weight. | release, dependency-weight |

## Score Anchors

Use these descriptions as **guidance**, not rules. The final score is your judgment.

### 0 – 2 (Healthy / Minor issues)

- The dimension is in good shape.
- Issues found are isolated, low-severity, and easy to fix.
- No structural debt. No systemic risk.
- **One-sentence pattern:** "Solid. A few minor issues but nothing that blocks release."

### 3 – 4 (Fair / Needs attention)

- Some real issues exist, but they are contained.
- Moderate risk in specific areas. No systemic failure.
- Fixing requires local changes, not rewrites.
- **One-sentence pattern:** "Some real issues, but contained. Worth fixing before next release."

### 5 – 6 (Poor / Significant risk)

- Systemic issues in this dimension.
- Multiple medium-or-higher severity findings.
- The dimension needs deliberate investment, not just quick fixes.
- **One-sentence pattern:** "Systemic problems. Needs deliberate investment, not quick patches."

### 7 – 8 (Bad / Critical debt)

- Serious failures in this dimension.
- High-severity issues that are not isolated — they indicate a pattern.
- Fixing requires structural changes.
- **One-sentence pattern:** "Structural failures. Fixing requires meaningful rework, not spot fixes."

### 9 – 10 (Shit Mountain / Unacceptable)

- This dimension is a disaster.
- Critical-severity issues that are pervasive.
- The approach in this dimension is fundamentally wrong.
- **One-sentence pattern:** "Fundamentally broken. Needs to be redone."

## Overall Score

Average of all 7 dimension scores, rounded to 1 decimal place.

For focused audit modes (e.g., security-only), only report the relevant dimension score and note that other dimensions were not assessed.

## Grade Map

| Score | Grade | Label | Meaning |
|-------|-------|-------|---------|
| 0.0 – 1.9 | S | Clean | Production-ready. Minor nitpicks only. |
| 2.0 – 3.9 | A | Good | Solid. Some issues but low urgency. |
| 4.0 – 5.9 | B | Fair | Needs work. Medium risks present. |
| 6.0 – 7.9 | C | Poor | Significant risks. Should address before release. |
| 8.0 – 9.4 | D | Bad | Critical issues. Do not ship as-is. |
| 9.5 – 10.0 | F | Shit Mountain | High-severity issues across the board. Major rework needed. |

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
Security        ████████░░  8.0  D
Stability       ██████░░░░  6.0  C
Performance     █████████░  9.0  D
Testing         ████░░░░░░  4.0  B
Maintainability ███████░░░  7.0  C
Design          █████░░░░░  5.0  B
Release         ██████░░░░  6.0  C
────────────────────────────────────
Overall         ██████░░░░  6.4  C
```

## Rules

1. **Each score must have a one-sentence justification** in the score dashboard (e.g., "Security: 8.0 — No auth on WebSocket, hardcoded JWT secret in config"). The justification summarizes the strongest evidence.
2. **Do not average finding severities.** If there is 1 Critical issue and nothing else, the score is not "10.0 - 2.0 = 8.0". Judge based on whether that one issue is systemic or isolated.
3. **Consider intensity and density.** 10 low-severity issues in one file may deserve a higher score than 1 critical issue with a trivial fix.
4. **Consider context.** A 600-line file in a CLI tool is different from a 600-line file in a security-critical library. Adjust for project type and scale.
5. **If a dimension has zero findings, score 0.0 (Clean).** But confirm you actually checked — absence of evidence is not evidence of absence.
6. **Do not round to game the grade.** If the score is 5.9, show 5.9, not 6.0. If it's 6.0, show 6.0.
7. **Include the score dashboard in the Executive Summary** with one-sentence justifications per dimension.
8. **Focused audit modes** (security-only, etc.): only score the relevant dimension. State "not assessed" for others.
