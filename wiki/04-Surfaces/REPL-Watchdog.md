---
aliases:
  - REPL Watchdog
  - Watch Commands
tags:
  - opensre/surfaces
  - opensre/watchdog
type: note
updated: 2026-07-26
---

# 👁️ REPL Watchdog Commands (`/watch`, `/watches`, `/unwatch`)

The REPL watchdog allows users to register continuous background health monitors directly from the interactive terminal interface.

---

## ⚡ Slash Commands

| Command | Usage | Description |
| :--- | :--- | :--- |
| `/watch <target> <threshold>` | `/watch service:auth cpu > 85%` | Spawns a background watchdog task monitoring specified target metrics. |
| `/watches` | `/watches` | Lists all active background watchdog monitors and their current status. |
| `/unwatch <id>` | `/unwatch w-102` | Terminates and removes a running watchdog background monitor. |

---

## 🔗 Related Notes
- [[Interactive-REPL|Interactive REPL Terminal]]
- [[System-Tools|System Tools & WatchDog]]
