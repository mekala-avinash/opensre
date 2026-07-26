---
aliases:
  - Naming Conventions
  - Glossary
  - Type Naming Rules
tags:
  - opensre/architecture
  - opensre/naming
type: note
updated: 2026-07-26
---

# 🏷️ Naming Conventions & Domain Glossary

OpenSRE strictly standardizes type names, domain terminology, and module file patterns to eliminate ambiguity across `core/`, `tools/`, and `integrations/`.

> [!note] Source File
> See [docs/NAMING.md](file:///Users/amekala/Desktop/opensre/docs/NAMING.md) for full context.

---

## 📖 Domain Glossary

| Term | Definition | Primary Module |
| :--- | :--- | :--- |
| `AgentState` | Immutable runtime state envelope containing chat history, tool calls, and investigation state. | `core/state/state.py` |
| `Snapshot` | A frozen point-in-time view of state passed to tools or rendering surfaces. | `core/state/snapshot.py` |
| `RunInput` | User-provided input parameters for initializing an investigation or turn. | `core/domain/types/` |
| `RunResult` | The final structured output of an investigation turn. | `core/domain/types/` |
| `EvidenceEntry` | Structured evidence record collected during tool calls (logs, metrics, alerts). | `core/state/evidence.py` |
| `Slice` | Isolated sub-state slice attached to `AgentState` (e.g. `InvestigationSlice`). | `core/state/slices.py` |

---

## 📁 File Naming Pattern

Modules under `core/` and `tools/` follow the **`{domain}_{role}.py`** pattern:

- **Good**: `investigation_lifecycle.py`, `context_budget.py`, `llm_credentials.py`
- **Bad**: `utils.py`, `helpers.py`, `misc.py` (Avoid generic dumping ground modules!)

---

## 📐 Type Naming Rules

1. **Protocol types**: Role-named without `I` prefix (e.g., `OutputSink`, `ToolRegistry`, not `IToolRegistry`).
2. **Mixins**: Suffix with `Mixin` (e.g. `StateUpdateMixin`).
3. **HTTP Status Codes**: Always use `http.HTTPStatus` (e.g., `HTTPStatus.PAYMENT_REQUIRED`), **never** hardcoded numeric literals like `402`.

---

## 🔗 Related Notes
- [[Architecture-Overview|Architecture Overview]]
- [[Layer-Stack|Layer Stack Detail]]
- [[Agent-State|Agent State Architecture]]
