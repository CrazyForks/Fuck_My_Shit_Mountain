# Release Audit Prompt

## Required: Ask Before Auditing

**STOP. Do not read any code yet. You must ask the user these questions first:**

1. **Audit modes** — Present the FULL list: `full`, `security`, `stability`, `performance`, `testing`, `maintainability`, `release`, `fallback`, `testing-authenticity`, `type-safety`, `frontend-state`, `backend-api`, `dependency-weight`. Ask: "Which mode(s)? Pick one or comma-separated. This prompt is pre-configured for release but you can choose any."
2. **Language / framework** — Ask: "What language and framework does the project use?"
3. **File output** — Ask: "Should I save the report to an .md file or print to stdout?"

Wait for answers before proceeding.

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

1. **Be exhaustive.** Check every CI step, every script, every config file. One missing env var can break production.
2. **Do not be a yes-man.** Report release risks even if the user says "we've never had a problem." Past success does not guarantee future safety.

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
