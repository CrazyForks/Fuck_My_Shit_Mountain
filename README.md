# Fuck My Shit Mountain 🏔️💩

> An evidence-based AI code audit skill. Professional output. Zero emotional bullshit.

**Fuck My Shit Mountain** is an AI skill (prompt framework) designed to produce rigorous, professional code reviews. Despite the intentionally crude name, every audit report is冷静 (calm), structured, evidence-driven, and actionable.

## What It Does

Feed it any codebase — it will analyze it across security, stability, performance, testing, maintainability, design principles, and release readiness. Each finding comes with:

- Concrete evidence (file, function, code behavior)
- Severity & confidence ratings
- Confirmed vs. suspected distinction
- Dimension scores (0.0–10.0) with letter grades
- Minimal fix + long-term fix
- Regression test suggestion
- Estimated effort

No empty complaints. No "this code is bad" without proof. No default rewrites.

## Quick Start

```text
Use fuck-my-shit-mountain in full mode.
Audit this repository for stable release readiness.
```

### Modes

| Mode | Focus |
|------|-------|
| `full` | Complete audit across all dimensions + 6 specialized areas |
| `fallback` | Silent fallback, catch, defensive guessing |
| `testing-authenticity` | Real test confidence vs green checkmarks |
| `type-safety` | Unsafe blocks, type assertions, boundary types |
| `frontend-state` | Component size, state management, effects |
| `backend-api` | API design, validation, data access patterns |
| `dependency-weight` | Overweight deps, build toolchain |
| `security` | Authentication, injection, secrets, dependencies |
| `stability` | Panic paths, error handling, concurrency, lifecycle |
| `fallback` | Silent fallback, catch, defensive guessing, compatibility branches |
| `testing-authenticity` | Over-mocking, implementation-detail tests, false confidence |
| `type-safety` | Unsafe blocks, type assertions, error types, input boundaries |
| `frontend-state` | Component size, state duplication, effects, UI-business coupling |
| `backend-api` | API consistency, request validation, N+1, data flow |
| `dependency-weight` | Overweight deps, unused deps, build toolchain complexity |
| `performance` | Hot paths, memory, I/O, startup cost |
| `testing` | Coverage quality, test types, flakiness |
| `maintainability` | Complexity, coupling, duplication, naming |
| `release` | CI/CD, versioning, upgrade, rollback |

## Project Structure

```
fuck-my-shit-mountain/
├── SKILL.md              — Skill entry point & rules
├── prompts/              — One prompt per audit mode (13 files)
├── rubrics/              — Severity, confidence, evidence, principles & scoring
├── templates/            — Report, issue card & remediation plan
└── examples/             — Rust, Node.js, Vue audit examples
```

## Usage with AI Tools

Works with **Codex**, **Claude Code**, **Cursor**, **Superpower**, or any AI that can follow structured prompts.

1. Load the skill: `SKILL.md`
2. Pick a mode: `prompts/full-audit.md` (or a focused one)
3. Paste the combined prompt + your codebase into the AI
4. Get a structured, evidence-backed audit report

## Sample Score Dashboard

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

## Design Principles

- **Evidence over opinion** — every finding cites file, function, and behavior
- **Separate signal from noise** — confirmed vs. suspected, never conflate
- **Smallest practical fix** — prefer local fixes, not rewrites
- **Test every finding** — every issue includes a regression test suggestion
- **No emotional language** — audit the code, not the author

## License

MIT
