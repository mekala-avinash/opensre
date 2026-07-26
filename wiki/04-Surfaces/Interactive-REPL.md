---
aliases:
  - Interactive REPL
  - REPL Terminal
  - Interactive Shell
tags:
  - opensre/surfaces
  - opensre/repl
type: note
updated: 2026-07-26
---

# 🖥️ Interactive REPL Terminal UI

The interactive shell (`surfaces/interactive_shell/`) provides a stateful REPL terminal interface equipped with live rendering, action selection, and slash commands.

---

## 🎮 Key Features

- **Stateful Conversation**: Retains investigation context across multiple command turns.
- **Rich Output Formatting**: Renders markdown tables, log highlights, and progress spinners.
- **Slash Commands**: Instant shortcuts for administrative and monitoring actions (`/watch`, `/watches`, `/unwatch`, `/help`).

---

## 🔗 Related Notes
- [[REPL-Watchdog|REPL Watchdog Commands]]
- [[Action-Planner-Policy|Action Planner & Turn Policy]]
- [[CLI-Runner|CLI Runner]]
