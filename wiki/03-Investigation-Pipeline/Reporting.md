---
aliases:
  - Incident Reporting
  - Reporting Engine
tags:
  - opensre/investigation
  - opensre/reporting
type: note
updated: 2026-07-26
---

# 📑 Incident Reporting & Post-Mortem Generation

The reporting subsystem (`tools/investigation/reporting/`) formats complete investigation results into structured formats tailored for human engineers, incident channels, and automated systems.

---

## 🎨 Report Formats

1. **Terminal Markdown**: Rich formatted terminal output with colored tables, timeline callouts, and code diffs.
2. **JSON Incident Payload**: Machine-readable JSON summary for integration with PagerDuty, Jira, or ServiceNow.
3. **Slack & Telegram Cards**: Markdown blocks optimized for mobile and desktop chat rendering.

---

## 🔗 Related Notes
- [[Pipeline-Lifecycle|Pipeline Lifecycle]]
- [[Telegram-and-Slack-Sinks|Telegram & Slack Sinks]]
