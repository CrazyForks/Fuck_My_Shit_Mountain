# Fuck My Shit Mountain

An AI-powered code audit skill that produces **professional, evidence-based, actionable** code reviews. Despite the crude name, the output is冷静, structured, and engineering-rigorous.

## What It Does

- Audits a codebase across **17 audit dimensions** (full mode): architecture, security, stability, performance, testing, maintainability, design, release, documentation, configuration, observability, fallback, testing-authenticity, type-safety, frontend-state, backend-api, dependency-weight
- Produces structured findings with severity, confidence, evidence, and fix recommendations
- Scores **7 core dimensions** (0.0–10.0) with letter grades for at-a-glance health assessment
- Separates confirmed issues from suspected issues
- Estimates fix effort and prioritizes risks
- Suggests regression tests for every finding

## Interactive Init

Before auditing, the AI **must ask 3 questions**:

1. **Which modes?** — Pick from 13 modes, comma-separated or `full`
2. **Report language?** — English / Chinese / etc.
3. **Output format?** — `md` / `html` / `both` / `stdout`

HTML output (`templates/audit-report.html`) provides a complete rendered page with sidebar navigation, scroll spy, colored score bars, per-dimension findings tables + verified checklists, design principles compliance, fix order tables, and quick wins grid.

## Usage

```
load fuck-my-shit-mountain/skill.md
run full-audit on .
```

### Mode Selection

| Command | Scope |
|---------|-------|
| `run full-audit` | All 17 audit dimensions |
| `run security-audit` | Security-only review |
| `run stability-audit` | Reliability and error handling |
| `run performance-audit` | Realistic performance bottlenecks |
| `run testing-audit` | Test quality and coverage gaps |
| `run maintainability-audit` | Code complexity and coupling |
| `run release-audit` | Release and deployment readiness |
| `run fallback-audit` | Silent fallback, catch, defensive guessing |
| `run testing-authenticity-audit` | Real test confidence vs green checkmarks |
| `run type-safety-audit` | Unsafe blocks, type assertions, boundary types |
| `run frontend-state-audit` | Component size, state management, effects |
| `run backend-api-audit` | API design, validation, data access patterns |
| `run dependency-weight-audit` | Overweight deps, build toolchain |

> Combine modes: `security, stability, type-safety` — the AI merges audit areas from each.

## Report Structure

A full audit report contains:

1. **Score Dashboard** — 7 dimension scores with bars + grades + one-sentence justification
2. **Stats** — Total findings by severity
3. **Top Risks** — Prioritized findings table
4. **Detailed Findings** — Every finding with full evidence, fix box, and test suggestion
5. **Per-Dimension Sections** — One `<h3>` per audited dimension with findings table + verified checklist
6. **Design Principles** — Violations table + followed principles check list
7. **Fix Order** — Grouped by urgency (immediate / pre-release / schedule / later)
8. **Quick Wins** — Low-cost high-value fixes

## File Structure

```
fuck-my-shit-mountain/
  SKILL.md              Skill entry point — how the skill works
  README.md             This file
  prompts/              Audit prompt templates (13 modes)
  rubrics/              Severity, confidence, evidence, principles, scoring
  templates/            Report, issue card, and remediation plan templates
  examples/             Usage examples for different project types
```

## Scoring

Each dimension scored 0.0–10.0 with letter grades (S/A/B/C/D/F):

```
Security        ████████░░  8.0  A   No auth on WS, hardcoded secret in config
Stability       ██████░░░░  6.0  B   3 unwrap on hot path, no retry on DB
Performance     ██████████  10.0 S   No issues found
Testing         ████░░░░░░  4.0  C   9 integration tests real, but unit is weak
Maintainability ███████░░░  7.0  A   3 files over 800 lines, SRP violated in 2 modules
Design          █████░░░░░  5.0  B   DRY violated 5x, fail-fast missing at API boundary
Release         ██████░░░░  6.0  B   No CI on Windows, no rollback plan
─────────────────────────────────────
Overall         ██████░░░░  6.6  B
```

Scoring is **judgment-based**, not formula-based. **Higher = better (10 = clean, 0 = shit mountain).** The AI evaluates evidence holistically, with a one-sentence justification per dimension. See `rubrics/scoring.md`.

## Rules of Engagement

- Every finding must have **concrete evidence**.
- No emotional language or personal attacks.
- No generic complaints about code quality.
- No default recommendation to rewrite.
- Distinguish **confirmed** from **suspected** issues.
- Include a **regression test suggestion** for every finding.
- Estimate **fix effort** for every finding.
