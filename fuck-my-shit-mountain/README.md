# Fuck My Shit Mountain

An AI-powered code audit skill that produces **professional, evidence-based, actionable** code reviews. Despite the crude name, the output is冷静, structured, and engineering-rigorous.

## What It Does

- Audits a codebase across security, stability, performance, testing, maintainability, design principles, and release readiness.
- Produces structured findings with severity, confidence, evidence, and fix recommendations.
- Scores each dimension (0.0–10.0) with letter grades for at-a-glance health assessment.
- Separates confirmed issues from suspected issues.
- Estimates fix effort and prioritizes risks.
- Suggests regression tests for every finding.

## Usage

### Prerequisites

- An AI coding assistant (Codex, Claude Code, Cursor, Superpower, etc.)
- Access to the target codebase

### Quick Start

```
# Full audit of the current project
load fuck-my-shit-mountain/skill.md
run full-audit on .
```

### Mode Selection

| Command | Scope |
|---------|-------|
| `run full-audit` | Complete audit across all dimensions + 6 specialized areas |
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

### Example

```text
Use the fuck-my-shit-mountain skill in full mode.

Audit this repository as if it is preparing for a stable public release.
```

## Report Structure

A full audit report contains:

1. **Executive Summary** — Score dashboard (7 dimensions) + finding statistics + short assessment.
2. **Project Map** — Architecture overview with risk areas highlighted.
3. **Top Risks** — 10-20 highest priority findings.
4. **Detailed Findings** — Every finding with full evidence.
5. **Testing Gaps** — Missing or weak tests.
6. **Security Concerns** — Confirmed and suspected security issues.
7. **Stability Concerns** — Crash, error handling, state consistency risks.
8. **Performance Concerns** — Realistic bottlenecks.
9. **Maintainability Concerns** — Complexity, coupling, duplication.
10. **Release Concerns** — CI/CD, versioning, deployment risks.
11. **Recommended Fix Order** — Grouped by urgency.
12. **Quick Wins** — Low-cost high-value fixes.
13. **Long-term Refactor Plan** — Only if evidence supports it.

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

Scoring is **judgment-based**, not formula-based. The AI evaluates evidence holistically, with a one-sentence justification per dimension. See `rubrics/scoring.md`.

## Rules of Engagement

- Every finding must have **concrete evidence**.
- No emotional language or personal attacks.
- No generic complaints about code quality.
- No default recommendation to rewrite.
- Distinguish **confirmed** from **suspected** issues.
- Include a **regression test suggestion** for every finding.
- Estimate **fix effort** for every finding.
