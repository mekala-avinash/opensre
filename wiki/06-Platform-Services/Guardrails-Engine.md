---
aliases:
  - Guardrails Engine
  - Safety Engine
  - Policy Enforcement
tags:
  - opensre/platform
  - opensre/guardrails
type: note
updated: 2026-07-26
---

# 🛡️ Platform Guardrails Engine

The Guardrails engine (`platform/guardrails/`) provides security rules, destructive action verification, and policy enforcement around all agent tool executions.

---

## 🎯 Policy Evaluation Flow

```mermaid
flowchart TD
    ToolCall["Agent Prepares Tool Call"] --> Guard["Guardrails Engine"]
    Guard --> Check1{"Contains Destructive Action?"}
    Check1 -- Yes --> Deny["BLOCK / Request User Confirmation"]
    Check1 -- No --> Check2{"Violates Resource Limits?"}
    Check2 -- Yes --> Deny
    Check2 -- No --> Allow["ALLOW Tool Execution"]
```

---

## 🔒 Action Rules

- **Destructive Commands**: `rm -rf`, database drops, production pod deletions require user approval or interactive confirmation.
- **Resource Constraints**: Limits max query time windows and restricts write actions during investigation stages.

---

## 🔗 Related Notes
- [[Agent-Loop|Agent ReAct Loop]]
- [[Data-Masking|Data Masking & Redaction]]
- [[Sandbox-Execution|Sandbox Execution]]
