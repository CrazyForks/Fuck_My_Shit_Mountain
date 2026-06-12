# Design Principles Audit Prompt

Use the fuck-my-shit-mountain skill in **design mode**.

Focus on practical violations of engineering principles from `rubrics/principles.md` that create correctness, maintainability, or release risk.

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

## Audit Areas

### Structure and Size Discipline
- SRP violations in functions, classes, modules, services, or components.
- Files/functions so large that behavior is hard to test or reason about.
- Excessive parameters, nesting, or cyclomatic complexity.
- Multiple unrelated reasons to change one unit.

### Coupling and Cohesion
- Modules that depend on too many unstable internal modules.
- Law of Demeter violations that couple callers to internal object shape.
- Concrete infrastructure dependencies inside high-level business logic.
- Interfaces that force clients to implement methods they do not use.

### Naming and Side Effects
- Names that hide mutation, I/O, network calls, persistence, or expensive work.
- Queries that also mutate state.
- Boolean traps and stringly typed state.
- Misleading abstractions that make failure modes surprising.

### Simplicity and Duplication
- Accidental duplication of real business rules.
- Over-engineered patterns without a current need.
- Abstractions with one implementation and no plausible second use.
- Complex generic code where a direct solution would reduce risk.

### Error and Boundary Design
- Invalid inputs traveling deep into the system before failing.
- Swallowed errors or lost error context.
- Generic public errors that prevent callers from handling failures.
- Missing fail-fast checks at external boundaries.

## Rules

1. Load `rubrics/principles.md` and cite exact principle IDs for findings.
2. Do not report principle violations that are only aesthetic.
3. Every design finding must explain the concrete change, bug, or test burden it creates.
4. Prefer local improvements over architecture rewrites.
5. A principle can be intentionally violated; accept it when the code documents and contains the tradeoff.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (Design and usually Maintainability). Per-dimension sections: one `<h3>` per relevant dimension, each with coverage note, findings table, and verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Design / Maintainability / Stability
- Status: Confirmed / Suspected
- Principle: <principle name and ID from rubrics/principles.md>
- Affected area:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Problem:
- Why this creates risk:
- Minimal fix:
- Regression test suggestion:
- Estimated effort:
