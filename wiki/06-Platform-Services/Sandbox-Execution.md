---
aliases:
  - Sandbox Execution
  - Execution Sandbox
tags:
  - opensre/platform
  - opensre/sandbox
type: note
updated: 2026-07-26
---

# 📦 Sandboxed Local Execution

`platform/sandbox/` isolates local command and Python execution tasks from the host machine operating system environment.

---

## 🔒 Isolation Safeguards

1. **Subprocess Isolation**: Restricts current working directory to workspace paths.
2. **Environment Variable Filtering**: Removes host environment secrets during subshell execution.
3. **Execution Timeouts**: Enforces hard wall-clock timeout caps (default: 30 seconds) on subprocess calls.

---

## 🔗 Related Notes
- [[System-Tools|System Tools & Python Execution]]
- [[Guardrails-Engine|Guardrails Engine]]
