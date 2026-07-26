---
aliases:
  - Investigation ReAct Loop
  - Stagnation Breaker
tags:
  - opensre/investigation
  - opensre/react
type: note
updated: 2026-07-26
---

# 🔄 Investigation ReAct Loop & Safeguards

The ReAct execution engine in `tools/investigation/` protects against infinite agent loops, tool repetition, and token budget exhaustion.

---

## 🛡️ Circuit Breaker Mechanisms

> [!warning] Stagnation Breaker
> If the agent invokes the exact same tool with identical arguments 3 times consecutively without acquiring new information, the stagnation breaker interrupts the turn and forces a hypothesis re-evaluation.

> [!important] Tool Execution Cap
> Investigations enforce a maximum ceiling of tool invocations per stage (default: 15 calls per stage) to prevent budget burn during unexpected provider failures.

---

## 🔗 Related Notes
- [[Agent-Loop|Core Agent Loop]]
- [[Pipeline-Lifecycle|Pipeline Lifecycle]]
