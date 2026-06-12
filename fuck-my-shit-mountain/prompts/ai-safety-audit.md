# AI and LLM Safety Audit Prompt

Use the fuck-my-shit-mountain skill in **ai-safety mode**.

Focus on AI/LLM application risks: prompt injection, tool authorization, RAG data leakage, model fallback, eval coverage, hallucination-sensitive workflows, and cost/abuse controls. Use this mode only when the project includes AI, LLM, agent, embedding, RAG, or model-serving behavior.

## Required Context Before Auditing

Before reading code, verify that audit mode(s), report language, and output format are known. If any are missing, ask only for the missing item(s) in one concise message and wait for the answer. If they are already supplied by the user or by the invoking skill, proceed without re-asking.

---

## Audit Areas

### Prompt and Instruction Boundaries
- Untrusted content is placed next to system/developer instructions without isolation.
- Retrieved documents, web pages, emails, tickets, or user files can override tool policy.
- Prompt templates concatenate role-like text or hidden directives unsafely.
- No separation between user intent, retrieved context, and execution policy.
- Sensitive instructions or chain-of-thought-like internals are exposed.

### Tool and Action Authorization
- Model output can trigger file, network, database, billing, email, or admin actions without policy checks.
- Tool arguments are trusted because they came from the model.
- Missing confirmation for irreversible or externally visible actions.
- Least-privilege scopes are not enforced per user/session/task.
- Tool results containing secrets are fed back into later prompts unnecessarily.

### RAG and Data Leakage
- Retrieval crosses tenant, account, workspace, or permission boundaries.
- Embeddings/indexes include sensitive data without deletion or access controls.
- Source attribution is missing for high-impact answers.
- Search filters are applied after retrieval instead of before.
- Cached model responses leak data across users or contexts.

### Model Reliability and Fallbacks
- Model fallback changes capability, cost, latency, or safety behavior silently.
- Outputs are used as facts without verification where correctness matters.
- JSON/function call parsing accepts malformed or partial outputs.
- No timeout, retry, or circuit breaker around model calls.
- No deterministic guardrail for safety-critical decisions.

### Evaluation and Monitoring
- No evals for prompt injection, data leakage, refusal/override, or tool misuse.
- Tests only assert happy-path text, not policy behavior.
- No logging/metrics for model errors, refusal rates, tool calls, token cost, or latency.
- No red-team corpus or regression suite for known failures.
- Production incidents cannot be traced to prompt/model/config version.

### Abuse and Cost Controls
- No rate limits, quotas, token budgets, or per-user spend tracking.
- Attackers can trigger expensive retrieval, long context, or recursive tool/model calls.
- Uploads or inputs can poison retrieval indexes.
- Moderation/safety checks are only applied after action execution.

## Rules

1. If the project has no AI/LLM surface, mark this mode Not assessed with evidence.
2. Every AI safety finding must identify attacker/user capability and the model/tool/data boundary crossed.
3. Do not rely on prompt wording alone as a security control for tool execution.
4. Prefer deterministic authorization, scoped retrieval, structured validation, evals, and budget limits.
5. Treat cross-tenant data leakage and unauthorized tool execution as High or Critical depending on blast radius.

## Format Constraint

**CRITICAL: The report MUST follow the skill's template format (`templates/issue-card.md` for findings, `templates/audit-report.md` or `.html` for the full report). Do NOT copy the formatting, heading style, or structure of any markdown file inside the audited project. The project's own docs are not the report template.**

For HTML output: read `templates/audit-report.html` and generate complete HTML that copies the exact structure. Score dashboard: one .score-item per dimension relevant to this mode (typically Security, Stability, Testing, and Performance). Per-dimension sections: one `<h3>` per relevant dimension, each with coverage note, findings table, and verified checklist. Design principles, fix order tables, quick wins grid, sidebar nav for every section. Do NOT use placeholder variables. Generate complete self-contained HTML.

## Finding Format

### Finding: <short title>

- Severity: Critical / High / Medium / Low / Info
- Confidence: High / Medium / Low
- Category: Security / Stability / Testing / Performance
- Status: Confirmed / Suspected
- Subtype: PromptInjection / ToolAuthorization / RAGLeakage / ModelFallback / OutputValidation / EvalGap / AbuseCost
- Boundary crossed:
- Evidence:
  - File:
  - Function / Module:
  - Relevant behavior:
- Attack or failure path:
- Minimal fix:
- Regression test suggestion:
- Estimated effort:
