# Documentation Audit Prompt

Use the fuck-my-shit-mountain skill in **documentation mode**.

Focus on whether external docs, internal docs, setup instructions, and operational guidance match the code and reduce real delivery risk.

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

## Audit Areas

### User and Operator Documentation
- README or docs describe commands, behavior, config, or APIs that no longer match code.
- Missing setup, install, upgrade, rollback, or deployment steps.
- Missing troubleshooting guidance for known failure modes.
- Operational docs lack health checks, alert handling, backup/restore, or incident response steps.

### Developer Documentation
- No architecture overview for non-obvious module boundaries.
- Missing contribution, test, build, or local environment instructions.
- Generated code, migrations, or scripts have no safe usage notes.
- Public extension/plugin APIs lack examples and compatibility expectations.

### API and Contract Documentation
- Endpoint, CLI, event, or config docs diverge from implemented contracts.
- Error responses, status codes, and auth requirements are not documented.
- Versioning and deprecation policy is missing.
- Examples use fields or payloads that the code no longer accepts.

### Decision Records
- Major tradeoffs are implicit and hard to rediscover.
- ADRs are missing for persistence, auth, concurrency, deployment, or public API choices.
- Old decisions remain documented after the implementation changes.
- Risky constraints have no documented mitigation or owner.

### Documentation Maintenance
- Docs duplicate source-of-truth data that could be generated.
- Stale badges, version numbers, feature lists, or screenshots.
- Comments and docs disagree with each other.
- No docs check in CI for generated or schema-derived docs.

## Rules

1. Documentation findings must compare docs against actual code or release behavior.
2. Prioritize misleading docs over missing docs.
3. Do not require heavyweight docs for a small private project unless missing guidance creates real risk.
4. Prefer linking docs to generated schemas/contracts when possible.
5. Include the exact doc location and the code/config it contradicts.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (typically Maintainability and Release). Per-dimension sections: one `<h3>` per relevant dimension, each with coverage note, findings table, and verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Maintainability / Release / Testing
- Status: Confirmed / Suspected
- Subtype: UserDocs / OperatorDocs / DeveloperDocs / ApiDocs / DecisionRecord / StaleDocs
- Affected area:
- Evidence:
  - Documentation file:
  - Code / config source:
  - Relevant mismatch or omission:
- Problem:
- Realistic failure scenario:
- Minimal fix:
- Regression test suggestion:
- Estimated effort:
