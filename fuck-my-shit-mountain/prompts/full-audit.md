# Full Audit Prompt

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

## Scoring

After collecting all findings, calculate dimension scores using `rubrics/scoring.md`:

1. Start each dimension at 10.0.
2. Deduct per finding based on severity and confidence status.
3. Render the score dashboard with ASCII bars and letter grades.
4. Include the dashboard in the Executive Summary.

## Output Format

Use the issue-card template for each finding. Assemble into the audit-report template.
