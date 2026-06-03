# Fuck My Shit Mountain — Skill Definition

## Purpose

Guide AI to perform an evidence-based, professional code audit of a software project. Despite the irreverent name, the output must be冷静 (calm), professional, actionable, and free of emotional language.

## Critical: You Must Ask Before Auditing

**Every prompt in this skill starts with a mandatory instruction: STOP and ask the user 3 questions before reading any code.**

The 3 questions are:

1. **Confirm audit scope** — Tell the user which mode this prompt corresponds to and confirm they want to proceed.
2. **Language / framework** — So the AI can use language-specific checklists and examples (e.g., Rust + Axum, Node.js + Express, Vue 3 + Pinia).
3. **File output** — Whether to save the report as `audit-report-<project>-<date>.md` in the current directory, or print to stdout. If yes, the AI MUST write the file after generating the report.

**Do not skip these questions. Do not assume the answers. Do not proceed until the user has responded to all 3.**

## How It Works

1. The user invokes the skill (or the AI asks the 3 init questions — **mandatory, do not skip**).
2. The AI loads the corresponding prompt from `prompts/`.
3. The AI audits the codebase using the rubrics in `rubrics/`.
4. Each finding is recorded using the template in `templates/issue-card.md`.
5. Results are assembled into a report using `templates/audit-report.md`.
6. If output-to-file was requested, the AI writes the report to disk.
7. If remediation is requested, the AI uses `templates/remediation-plan.md`.

## Modes

| Mode | Prompt | Focus |
|------|--------|-------|
| `full` | `prompts/full-audit.md` | All dimensions + principles |
| `security` | `prompts/security-audit.md` | Security risks |
| `stability` | `prompts/stability-audit.md` | Reliability & errors |
| `performance` | `prompts/performance-audit.md` | Realistic bottlenecks |
| `testing` | `prompts/testing-audit.md` | Test quality & gaps |
| `maintainability` | `prompts/maintainability-audit.md` | Complexity, coupling, principles |
| `release` | `prompts/release-audit.md` | Release readiness |
| `fallback` | `prompts/fallback-audit.md` | Silent fallback, catch, defensive guessing |
| `testing-authenticity` | `prompts/testing-authenticity-audit.md` | Real confidence vs green checkmarks |
| `type-safety` | `prompts/type-safety-audit.md` | Unsafe blocks, assertions, boundary types |
| `frontend-state` | `prompts/frontend-state-audit.md` | Component size, state, effects, coupling |
| `backend-api` | `prompts/backend-api-audit.md` | API design, validation, data access patterns |
| `dependency-weight` | `prompts/dependency-weight-audit.md` | Overweight deps, build toolchain |

## Scoring

Each audit produces a **score dashboard** with 7 dimension scores (0.0–10.0) and an overall score:

- Scores are **judgment-based**, not mechanical deductions. The AI evaluates evidence holistically per dimension.
- Each score must have a **one-sentence justification** referencing the strongest evidence.
- A letter grade (S/A/B/C/D/F) provides an at-a-glance health indicator.
- Scores supplement detailed findings — they do not replace them.

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
11. Check violations of engineering principles using `rubrics/principles.md` — focus on violations that create real risk, not minor style quarrels.
12. **Be exhaustive.** Search the entire codebase, not just the obvious hotspots. If you stop looking after finding a few issues, you are doing a disservice. Leave no file unchecked.
13. **Do not be a yes-man.** Do not suppress findings because the user seems confident, or because you want to be agreeable. Your job is to identify real risks objectively, regardless of who wrote the code or what the user expects to hear. If the code has problems, say so.
