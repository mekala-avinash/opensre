---
aliases:
  - Slack App
  - Slack Bot Surface
tags:
  - opensre/surfaces
  - opensre/slack
type: note
updated: 2026-07-26
---

# 💬 Slack Application Surface

`surfaces/slack_app/` implements an interactive Slack bot surface that allows teams to trigger investigations directly inside Slack incident channels.

---

## ⚡ Capability Breakdown

- Slash Command Handler (`/opensre investigate <alert_id>`).
- Mention Handler (`@OpenSRE investigate high latency on checkout service`).
- Interactive Block Kit UI buttons for approving remediation action plans.

---

## 🔗 Related Notes
- [[Gateway-Architecture|Gateway Daemon]]
- [[Telegram-and-Slack-Sinks|Telegram & Slack Sinks]]
