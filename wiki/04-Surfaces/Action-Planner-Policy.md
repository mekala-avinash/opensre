---
aliases:
  - Action Planner Policy
  - Turn Policy
  - No Fail Closed Rule
tags:
  - opensre/surfaces
  - opensre/policy
type: note
updated: 2026-07-26
---

# 📜 Action Planner Policy & No Fail-Closed Safeguard

The interactive shell action planner (`surfaces/interactive_shell/`) governs how user requests map to actions and capabilities.

> [!important] Crucial Invariant
> **No planning-stage fail-closed safeguard**: The interactive-shell action planner must NEVER deny a user turn, fail closed, or emit `mark_unhandled` / `UNHANDLED:` responses.

---

## 🎯 Policy Principles

1. Every user turn in the interactive shell is dispatched to the action agent harness.
2. Direct slash commands (e.g. `/watch`) short-circuit literal string matching before LLM dispatch.
3. For general queries, the action agent formulates a plan rather than denying the user request.

---

## 🔗 Related Notes
- [[Interactive-REPL|Interactive REPL Terminal]]
- [[Troubleshooting-and-FAQ|Troubleshooting & Footguns]]
