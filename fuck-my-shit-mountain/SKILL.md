# Fuck My Shit Mountain — Skill Definition

## Purpose

Guide AI to perform an evidence-based, professional code audit of a software project. Despite the irreverent name, the output must be冷静 (calm), professional, actionable, and free of emotional language.

## How It Works

1. The user selects an audit mode (full or focused).
2. The AI loads the corresponding prompt from `prompts/`.
3. The AI audits the codebase using the rubrics in `rubrics/`.
4. Each finding is recorded using the template in `templates/issue-card.md`.
5. Results are assembled into a report using `templates/audit-report.md`.
6. If remediation is requested, the AI uses `templates/remediation-plan.md`.

## Modes

| Mode | Prompt | Focus |
|------|--------|-------|
| `full` | `prompts/full-audit.md` | All dimensions |
| `security` | `prompts/security-audit.md` | Security risks |
| `stability` | `prompts/stability-audit.md` | Reliability & errors |
| `performance` | `prompts/performance-audit.md` | Realistic bottlenecks |
| `testing` | `prompts/testing-audit.md` | Test quality & gaps |
| `maintainability` | `prompts/maintainability-audit.md` | Complexity & coupling |
| `release` | `prompts/release-audit.md` | Release readiness |

## Rules (Non-negotiable)

1. Every finding MUST include concrete evidence (file, function, behavior).
2. Separate **Confirmed** issues from **Suspected** issues.
3. Do not exaggerate severity — map to `rubrics/severity.md`.
4. Do not recommend rewrites unless local fixes are clearly insufficient.
5. Prefer the smallest practical fix that reduces real risk.
6. Do not produce generic advice. Every finding must tie to a realistic failure scenario.
7. Do not complain about style unless it creates a demonstrable maintainability or correctness risk.
8. If evidence is insufficient, say so. Do not fabricate findings.
9. Every finding MUST include a regression test suggestion.
10. Every finding MUST include an estimated effort.
