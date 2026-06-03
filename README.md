# Fuck My Shit Mountain 🏔️💩

> An evidence-based AI code audit skill. Professional output. Zero emotional bullshit.

**Fuck My Shit Mountain** is an AI skill (prompt framework) designed to produce rigorous, professional code reviews. Despite the intentionally crude name, every audit report is冷静 (calm), structured, evidence-driven, and actionable.

## What It Does

Feed it any codebase — it will analyze it across security, stability, performance, testing, maintainability, and release readiness. Each finding comes with:

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
| `full` | Complete audit across all dimensions |
| `security` | Authentication, injection, secrets, dependencies |
| `stability` | Panic paths, error handling, concurrency, lifecycle |
| `performance` | Hot paths, memory, I/O, startup cost |
| `testing` | Coverage quality, test types, flakiness |
| `maintainability` | Complexity, coupling, duplication, naming |
| `release` | CI/CD, versioning, upgrade, rollback |

## Project Structure

```
fuck-my-shit-mountain/
├── SKILL.md              — Skill entry point & rules
├── prompts/              — One prompt per audit mode (7 files)
├── rubrics/              — Severity, confidence, evidence & scoring standards
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
Security        ████████░░  8.0  A
Stability       ██████░░░░  6.0  B
Performance     █████████░  9.0  S
Testing         ████░░░░░░  4.0  C
Maintainability ███████░░░  7.0  A
Release         ██████░░░░  6.0  B
────────────────────────────────────
Overall         ███████░░░  6.7  B
```

## Design Principles

- **Evidence over opinion** — every finding cites file, function, and behavior
- **Separate signal from noise** — confirmed vs. suspected, never conflate
- **Smallest practical fix** — prefer local fixes, not rewrites
- **Test every finding** — every issue includes a regression test suggestion
- **No emotional language** — audit the code, not the author

## License

MIT
