# Fuck My Shit Mountain 🏔️💩

> An evidence-based AI code audit skill. Professional output. Zero emotional bullshit.

**Fuck My Shit Mountain** is an AI skill (prompt framework) that produces rigorous, professional code reviews. Despite the crude name, every report is冷静, structured, evidence-driven, and actionable.

## How It Works

1. **AI asks 3 questions** before touching any code: which modes, what language, what output format (md/html/both/stdout)
2. **AI audits your codebase** exhaustively — every file, every function
3. **AI generates a structured report** with scores, findings, principles, fix order, and quick wins
4. **HTML output** includes a sidebar with scroll spy, colored score bars, per-dimension sections with findings tables + verified checklists, design principles compliance, and a fix order table

## Modes

Pick one or combine (e.g., `security, stability, type-safety`). Full mode covers **17 audit dimensions**.

| Mode | Focus |
|------|-------|
| `full` | All 17 dimensions |
| `security` | Authentication, injection, secrets, dependencies |
| `stability` | Panic paths, error handling, concurrency, lifecycle |
| `performance` | Hot paths, memory, I/O, startup cost |
| `testing` | Coverage quality, test types, flakiness |
| `maintainability` | Complexity, coupling, duplication, naming |
| `release` | CI/CD, versioning, upgrade, rollback |
| `fallback` | Silent fallback, catch, defensive guessing |
| `testing-authenticity` | Over-mocking, impl-detail tests, false confidence |
| `type-safety` | Unsafe blocks, type assertions, boundary types |
| `frontend-state` | Component size, state duplication, effects, coupling |
| `backend-api` | API consistency, validation, N+1, data flow |
| `dependency-weight` | Overweight deps, build toolchain |

## Project Structure

```
fuck-my-shit-mountain/
├── SKILL.md              — Entry point & rules
├── prompts/              — 13 audit mode prompts
├── rubrics/              — Severity, confidence, evidence, principles, scoring
├── templates/            — audit-report.md, audit-report.html, issue-card.md, remediation-plan.md
└── examples/             — Rust, Node.js, Vue audit examples
```

## Sample Score Dashboard

```
Security        ████████░░  8.0  A
Stability       ██████░░░░  6.0  B
Performance     ██████████  10.0 S
Testing         ████░░░░░░  4.0  C
Maintainability ███████░░░  7.0  A
Design          █████░░░░░  5.0  B
Release         ██████░░░░  6.0  B
─────────────────────────────────────
Overall         ██████░░░░  6.6  B
```

**Higher = better (10 = clean, 0 = shit mountain).** Scores are judgment-based, not formula-based.

See `fuck-my-shit-mountain/rubrics/scoring.md` for anchor descriptions and letter grade map.

## License

MIT
