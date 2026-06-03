# Maintainability Audit Prompt

Use the fuck-my-shit-mountain skill in **maintainability mode**.

Focus on maintainability, complexity, coupling, and design risk.

## Audit Areas

### Size & Structure
- Files over 500 lines
- Functions over 50 lines
- Functions with deep nesting (4+ levels)
- Files with too many responsibilities
- Modules with unclear boundaries

### Complexity
- Cyclomatic complexity hotspots
- Functions with too many parameters (4+)
- Functions with too many branches / conditions
- Complex conditional logic
- Deeply nested callbacks or promises
- Overuse of dynamic features (eval, reflection, metaprogramming)

### Coupling & Cohesion
- Hidden dependencies between modules
- Circular dependencies
- Tight coupling to external libraries or frameworks
- God objects / classes with too many responsibilities
- Shotgun surgery — one change requires touching many files
- Feature envy — a function that mostly uses data from another module

### Duplication
- Repeated logic that should be abstracted
- Copy-pasted code with minor variations
- Duplicated configuration or constants
- Parallel hierarchies that mirror each other

### Naming & Documentation
- Misleading names that do not reflect behavior
- Names that hide side effects (e.g., `getX()` that mutates state)
- Missing documentation on non-obvious behavior
- Documentation that contradicts the code
- Comments that explain "what" instead of "why"

### Design Patterns
- Business logic mixed with transport (HTTP, CLI, message queue)
- Business logic mixed with persistence (SQL, file I/O)
- Business logic mixed with UI rendering
- Leaky abstractions that expose implementation details
- Premature abstraction (generic where specific is sufficient)
- Over-engineering (unnecessary indirection, patterns, frameworks)

### Changeability
- Code that is difficult to delete (too many callers, unclear ownership)
- Special-case logic scattered across the codebase
- Configuration scattered instead of centralized
- Default values duplicated across code paths
- Feature flags that are never cleaned up

## Rules

1. Do not recommend abstraction unless it removes real duplication, coupling, or confusion.
2. For each issue, include the risk of changing the code and the test needed before refactoring.
3. Prefer local improvements over architectural rewrites.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Maintainability
- Status: Confirmed / Suspected
- Affected area:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Why this affects maintainability:
- Risk of changing it:
- Local fix:
- Better long-term fix:
- Test needed before refactor:
- Estimated effort:
