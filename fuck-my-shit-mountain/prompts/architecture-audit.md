# Architecture Audit Prompt

Use the fuck-my-shit-mountain skill in **architecture mode**.

Focus on module boundaries, dependency direction, layering, ownership, and whether the system shape supports safe change.

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

## Audit Areas

### Module Boundaries
- Modules with unclear ownership or overlapping responsibilities.
- Domain logic spread across UI, API handlers, database adapters, and scripts.
- "Utils" or "common" modules that hide unrelated behavior.
- Public APIs exposing implementation details.
- Cross-layer imports that bypass intended boundaries.

### Dependency Direction
- High-level policy depending directly on low-level infrastructure.
- Circular imports or package cycles.
- Feature modules depending on unstable internals from other features.
- Test-only architecture seams leaking into production design.
- Global singletons used instead of explicit dependencies.

### Data and State Ownership
- Multiple modules mutating the same state without a clear owner.
- Ambiguous source of truth for cached/derived data.
- Shared mutable state crossing async/thread/process boundaries.
- Persistence models reused as API or UI models where that creates coupling.
- State transitions implemented in multiple places.

### Boundary Contracts
- Missing contracts between layers, packages, services, or plugins.
- Implicit serialization formats or event payloads.
- Adapters that do validation/business logic inconsistently.
- Backward compatibility assumptions not documented or enforced.
- Runtime feature discovery where explicit interfaces would be safer.

### Evolution and Extensibility
- Adding a feature requires editing many unrelated modules.
- Extension points are too generic or too rigid.
- Architecture decisions are encoded only in tribal knowledge.
- Dead abstractions with one implementation and no realistic second use.
- Migration paths between old and new architecture are unclear.

## Rules

1. Judge architecture relative to project size and release stage.
2. Do not recommend rewrites unless local boundary repairs are clearly insufficient.
3. Cite concrete dependency paths, import cycles, state owners, or change scenarios.
4. Prefer small moves: introduce an interface, move validation to a boundary, split one module, or invert one dependency.
5. If a design is simple and works for the scale, do not over-architect it.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (typically Maintainability and Design). Per-dimension sections: one `<h3>` per relevant dimension, each with coverage note, findings table, and verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Maintainability / Design / Stability
- Status: Confirmed / Suspected
- Subtype: ModuleBoundary / DependencyDirection / StateOwnership / BoundaryContract / EvolutionRisk
- Affected area:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Problem:
- Realistic change scenario:
- Minimal fix:
- Regression test suggestion:
- Estimated effort:
