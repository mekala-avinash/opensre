---
aliases:
  - Telegram and Slack Sinks
  - Output Sinks
  - Message Redaction Boundary
tags:
  - opensre/gateway
  - opensre/sinks
type: note
updated: 2026-07-26
---

# 💬 Telegram & Slack Output Sinks

`gateway/telegram` and `gateway/slack` provide message rendering and output sinks (`OutputSink`) for external chat platforms.

---

## 🛡️ Error Redaction at the Sink Boundary

> [!important] CWE-209 Prevention Rule
> **Never leak raw stack traces or internal exception details to external chat sinks.**
> External surfaces (`OutputSink.render_error` on Telegram/Slack and HTTP responses in `gateway/http/`) must redact sensitive traceback details (`str(exc)`, `traceback.format_exc()`). Log full exception details server-side, but return only generic error messages or `type(exc).__name__` to chat users.

---

## 🔗 Related Notes
- [[Gateway-Architecture|Gateway Architecture]]
- [[Troubleshooting-and-FAQ|Troubleshooting & Footgun Guide]]
