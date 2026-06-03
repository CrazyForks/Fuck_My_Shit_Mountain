# Full Audit Prompt

## Required: Ask Before Auditing

**STOP. Do not read any code yet. You must ask the user these 3 questions first:**

1. **Confirm scope** — Ask: "Full audit — covers all 17 dimensions (security, stability, performance, testing, maintainability, design, release, fallback, testing-authenticity, type-safety, frontend-state, backend-api, dependency-weight). Proceed?"
2. **Language / framework** — Ask: "What language and framework does the project use?"
3. **File output** — Ask: "Should I save the report to an .md file or print to stdout?"

Wait for answers before proceeding.

---

Use the fuck-my-shit-mountain skill in **full mode**.

Audit this repository as if it is preparing for a stable public release.

Your job is not to insult the codebase. Your job is to identify real engineering risks with evidence.

## Setup

Before writing findings, build a project map:

- Main components and their responsibilities
- Runtime entry points and initialization order
- Data flow — request/event lifecycle
- State ownership — what owns what state, how it is mutated
- Persistence layer — storage format, migration strategy, backup
- External interfaces — APIs, WebSocket, CLI, file system, network
- Security boundaries — authentication, authorization, input validation, secret management
- Testing structure — test organization, coverage patterns, CI integration
- Release process — versioning, build, packaging, deployment, rollback

## Audit Dimensions

1. **Architecture and module boundaries** — cohesion, coupling, dependency direction, layered architecture
2. **Security** — authentication, authorization, injection, secret handling, dependency risks
3. **Stability and error handling** — panic paths, error propagation, retry, timeout, shutdown
4. **Performance and scalability** — hot paths, growth limits, resource leaks, contention
5. **Testing quality** — coverage, test types, flakiness, confidence
6. **Maintainability** — complexity, duplication, naming, documentation accuracy
7. **Design principles compliance** — check `rubrics/principles.md` for SRP, file size, function length, coupling, cohesion, DRY, YAGNI, KISS, fail-fast, command-query separation, law of demeter, and all other principles
8. **Release and deployment process** — CI/CD, versioning, upgrade, rollback
9. **Documentation accuracy** — does the docs match the code?
10. **Configuration safety** — defaults, environment separation, validation
11. **Observability** — logging, metrics, tracing, debugging support
12. **Fallback / defensive code audit** — check `prompts/fallback-audit.md` for silent fallbacks, empty catches, compatibility branches, and defensive guessing that hides real errors
13. **Testing authenticity audit** — check `prompts/testing-authenticity-audit.md` for over-mocking, implementation detail tests, production code modified for tests, and false confidence
14. **Type safety audit** — check `prompts/type-safety-audit.md` for unsafe blocks, type assertions, boundary weakness, and error type quality
15. **Frontend state audit** (if applicable) — check `prompts/frontend-state-audit.md` for component size, state duplication, effect proliferation, and UI-business logic coupling
16. **Backend API audit** (if applicable) — check `prompts/backend-api-audit.md` for API consistency, request validation, data access patterns, and error response structure
17. **Dependency weight audit** — check `prompts/dependency-weight-audit.md` for overweight deps, unused deps, build toolchain complexity, and version strategy

## Rules

1. Every finding must include concrete evidence (file, function, behavior).
2. Separate confirmed issues from suspected issues.
3. Do not exaggerate severity. Use the severity rubric.
4. Do not recommend rewrites unless local fixes are clearly insufficient.
5. Prefer the smallest practical fix that reduces real risk.
6. Do not produce generic advice.
7. Do not complain about style unless it creates maintainability risk.
8. If evidence is insufficient, say so.
9. For each issue, include a regression test suggestion.
10. Prioritize the top risks first.
11. Cross-reference findings against `rubrics/principles.md`. For each principle violation, cite the specific principle (e.g., "SRP violation — principle 1.1").

## Attitude

1. **Be exhaustive.** Search the entire codebase, not just obvious hotspots. Every file, every function. Leave no stone unturned.
2. **Do not be a yes-man.** Do not suppress findings to be agreeable. Report issues objectively regardless of who wrote the code. If the code has problems, say so.

## Scoring

After collecting all findings, assign dimension scores using `rubrics/scoring.md`:

1. Review all findings per dimension.
2. Judge the score (0.0–10.0, where 10 = worst) based on **engineering risk and maintenance cost**, not on mechanical deduction.
3. Each score must have a **one-sentence justification** summarizing the strongest evidence.
4. Render the score dashboard with ASCII bars and letter grades.
5. Include the dashboard with justifications in the Executive Summary.

## Output Format

Use the issue-card template for each finding. Assemble into the audit-report template.
