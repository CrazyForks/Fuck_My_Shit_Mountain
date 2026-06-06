# Release Audit Prompt

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

Use the fuck-my-shit-mountain skill in **release mode**.

Focus on whether this project can be safely released, installed, upgraded, and rolled back.

## Audit Areas (see principles 9.1–9.3: Configuration & Environment)

### CI/CD Pipeline
- What checks run in CI? (lint, typecheck, test, build, security scan)
- Are there gates before merge? Before release?
- Build matrix (OS, architecture, language version)
- Artifact caching and reproducibility
- CI speed — does it discourage frequent releases?

### Versioning
- Version scheme (semver, date-based, commit-based)
- Version defined where and how
- Pre-release handling (alpha, beta, rc)
- Version bump automation
- Breaking change detection
- Changelog generation

### Build & Artifacts
- Build script correctness and determinism
- Dependency vendoring or lockfile
- Artifact naming and storage
- Checksum / signature generation
- SBOM generation
- Binary / package provenance

### Installation
- Install script safety (no curl-bash without verification)
- Package manager registration (npm, cargo, pip, docker)
- Minimum supported version documentation
- Dependency resolution and conflicts
- First-run experience

### Upgrade Path
- Data migration (schema, config, state format)
- Backward compatibility period
- Deprecation policy
- Config file format migration
- State / database migration rollback

### Rollback
- Can a release be rolled back?
- Is the previous artifact available?
- Data migration reversibility
- Config migration reversibility
- Rollback testing

### Deployment
- Dockerfile quality (multi-stage, layer caching, non-root user)
- Service definition (systemd, launchd, kubernetes)
- Environment variable configuration
- Health check endpoint
- Startup probe, readiness probe, liveness probe
- Resource limits

### Compatibility
- API versioning strategy
- Breaking change communication
- Documentation of compatibility guarantees
- Deprecation notice period

## Rules

1. Focus on practical release risks, not hypothetical edge cases.
2. For each issue, include the user impact and a specific validation step.

## Attitude

1. **Be exhaustively systematic.** Check in-scope CI steps, release scripts, environment requirements, config files, packaging, rollback, and deployment evidence. Follow the skill's coverage strategy and document exclusions honestly.
2. **Do not be a yes-man.** Report release risks even if the user says "we've never had a problem." Past success does not guarantee future safety.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (NOT all 7 — only the dimensions this mode audits). Per-dimension sections: one `<h3>` per relevant dimension, each with findings table + verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Release
- Status: Confirmed / Suspected
- Affected area:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Release risk:
- User impact:
- Minimal fix:
- Better release process:
- Validation step:
- Estimated effort:
