# Privacy and Data Governance Audit Prompt

Use the fuck-my-shit-mountain skill in **privacy mode**.

Focus on personal data handling, data minimization, retention, deletion, export, logging, access boundaries, and privacy-relevant governance.

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

## Audit Areas

### Data Inventory and Classification
- PII or sensitive data collected without a clear purpose.
- Personal data fields stored without classification or ownership.
- Sensitive fields copied into analytics, logs, caches, queues, or exports.
- Test fixtures or examples contain realistic personal data.
- Derived identifiers can re-identify users.

### Data Minimization
- Collecting or persisting fields not needed for current behavior.
- Sending full records where only IDs or aggregates are needed.
- Retaining raw payloads after extraction.
- Third-party integrations receive unnecessary user data.
- Debug/admin tools expose full records by default.

### Consent, Access, and Purpose Boundaries
- Privacy-sensitive processing has no user/account-level gate.
- Internal roles can access more data than their job requires.
- Admin or support tooling lacks audit logs.
- Data is reused across features without a clear purpose boundary.
- Tenant/account boundaries are not enforced in privacy-sensitive queries.

### Retention, Deletion, and Export
- No retention period for logs, events, uploads, or backups.
- Delete requests do not remove derived data, caches, queues, or search indexes.
- Export misses important user data or includes other users' data.
- Backups make deletion guarantees misleading.
- Retention config differs from documented policy.

### Privacy in Logs and Telemetry
- PII appears in logs, traces, metrics labels, crash reports, or error responses.
- High-cardinality labels contain user identifiers.
- Correlation IDs can be linked to personal data without controls.
- Third-party telemetry SDKs send sensitive context by default.

## Rules

1. Privacy findings must identify the personal or sensitive data involved.
2. Do not cite legal compliance obligations unless the project explicitly targets that regime; describe engineering risk instead.
3. Treat PII in logs as both privacy and security risk.
4. Prefer data minimization, redaction, access control, retention config, and audit trails over broad rewrites.
5. If no personal data is processed, mark the mode Not assessed or Info with evidence.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (typically Security, Stability, and Release). Per-dimension sections: one `<h3>` per relevant dimension, each with coverage note, findings table, and verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Security / Stability / Release
- Status: Confirmed / Suspected
- Subtype: DataInventory / Minimization / AccessBoundary / Retention / Deletion / Export / TelemetryPrivacy
- Affected data:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Problem:
- Realistic privacy failure scenario:
- Minimal fix:
- Regression test suggestion:
- Estimated effort:
