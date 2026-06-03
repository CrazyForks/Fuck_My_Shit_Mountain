# Fuck My Shit Mountain Audit Report

**Project:** <project name>
**Audit mode:** <full / security / stability / performance / testing / maintainability / release>
**Date:** <date>
**Reviewer:** <AI model / version>

---

## 1. Executive Summary

<2-3 paragraph summary of codebase condition>

### Score Dashboard

```
Security        ████████░░  8.0  D   No auth on WS, hardcoded secret in config
Stability       ██████░░░░  6.0  C   3 unwrap on hot path, no retry on DB
Performance     █████████░  9.0  D   N+1 query per request, no pagination
Testing         ████░░░░░░  4.0  B   9 integration tests are real, but unit is weak
Maintainability ███████░░░  7.0  C   3 files over 800 lines, SRP violated in 2 modules
Design          █████░░░░░  5.0  B   DRY violated 5x, fail-fast missing at API boundary
Release         ██████░░░░  6.0  C   No CI on Windows, no rollback plan
────────────────────────────────────
Overall         ██████░░░░  6.4  C
```

Each dimension scored 0.0–10.0 (10 = worst). Scores are judgment-based, not formula-based. See `rubrics/scoring.md` for anchor descriptions.

### Finding Statistics

| Severity | Count | Confirmed | Suspected |
|----------|-------|-----------|-----------|
| Critical | <N> | <N> | <N> |
| High | <N> | <N> | <N> |
| Medium | <N> | <N> | <N> |
| Low | <N> | <N> | <N> |
| Info | <N> | <N> | <N> |
| **Total** | **<N>** | **<N>** | **<N>** |

## 2. Project Map

<How the project is structured — key components, entry points, data flow, state ownership, persistence, external interfaces, security boundaries>
<Highlight areas most likely to contain risks>

## 3. Top Risks

<5-15 findings in priority order. Each entry includes finding title, severity, and one-sentence summary. Full details in section 4.>

## 4. Detailed Findings

<All findings using the issue-card template>

## 5. <Dimension-specific section>

Depending on audit mode:

- **Full / Security:** Security Concerns
- **Full / Stability:** Stability Concerns
- **Full / Performance:** Performance Concerns
- **Full / Testing:** Testing Gaps
- **Full / Maintainability:** Maintainability Concerns
- **Full / Release:** Release Concerns
- **Security:** Security Concerns
- **Stability:** Stability Concerns
- **Performance:** Performance Concerns
- **Testing:** Testing Gaps
- **Maintainability:** Maintainability Concerns
- **Release:** Release Concerns

Each section lists relevant issues grouped by sub-category.

## 6. <Next dimension-specific section>

Repeat for all dimensions covered by the audit mode.

---

## <N+1>. Principles Compliance

<Summary of how well the codebase follows software engineering principles from rubrics/principles.md>

### Principles Violated

| Principle | Violations | Severity | Affected Areas |
|-----------|------------|----------|----------------|
| Single Responsibility (SRP) | <N> | Medium | <modules> |
| File Size Limit | <N> | Low | <modules> |
| Fail-Fast | <N> | High | <modules> |
| ... | ... | ... | ... |

### Principles Respected

<Principles that the codebase follows well — what is being done right>

---



## <N+2>. Recommended Fix Order

### Fix Immediately

<Issues that can cause data loss, security breach, or service outage>

### Fix Before Stable Release

<Issues that degrade reliability, correctness, or security>

### Schedule Later

<Issues that increase maintenance cost or limit scale>

### Ignore for Now

<Low-severity issues, theoretical risks, style preferences>

## <N+3>. Quick Wins

<Low-cost, high-value fixes — typically 1-2 hour changes that remove real risk>

## <N+4>. Long-term Refactor Plan

<Only included if evidence supports structural improvements>
<Each item includes: motivation, approach, risk, and testing strategy>
