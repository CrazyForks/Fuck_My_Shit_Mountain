# Fuck My Shit Mountain

An AI-powered code audit skill that produces **professional, evidence-based, actionable** code reviews. Despite the crude name, the output is冷静, structured, and engineering-rigorous.

## What It Does

- Audits a codebase across security, stability, performance, testing, maintainability, and release readiness.
- Produces structured findings with severity, confidence, evidence, and fix recommendations.
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
| `run full-audit` | Complete audit across all dimensions |
| `run security-audit` | Security-only review |
| `run stability-audit` | Reliability and error handling |
| `run performance-audit` | Realistic performance bottlenecks |
| `run testing-audit` | Test quality and coverage gaps |
| `run maintainability-audit` | Code complexity and coupling |
| `run release-audit` | Release and deployment readiness |

### Example

```text
Use the fuck-my-shit-mountain skill in full mode.

Audit this repository as if it is preparing for a stable public release.
```

## Report Structure

A full audit report contains:

1. **Executive Summary** — Short, direct assessment of codebase condition.
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
  prompts/              Audit prompt templates (one per mode)
  rubrics/              Severity, confidence, and evidence standards
  templates/            Report, issue card, and remediation plan templates
  examples/             Usage examples for different project types
```

## Rules of Engagement

- Every finding must have **concrete evidence**.
- No emotional language or personal attacks.
- No generic complaints about code quality.
- No default recommendation to rewrite.
- Distinguish **confirmed** from **suspected** issues.
- Include a **regression test suggestion** for every finding.
- Estimate **fix effort** for every finding.
