---
aliases:
  - Data Masking
  - Redaction Engine
tags:
  - opensre/platform
  - opensre/masking
type: note
updated: 2026-07-26
---

# 🎭 Sensitive Data Masking & PII Redaction

The masking engine (`platform/masking/`) scans all incoming and outgoing tool payloads to redact sensitive information before it reaches state models, message history, or external API endpoints.

---

## 🔍 Redacted Pattern Types

- **API Keys & Secrets**: AWS Secret Access Keys, Bearer tokens, GitHub Personal Access Tokens, RSA Private Keys.
- **Connection Strings**: Database URLs containing plaintext passwords (`postgres://user:pass@host...`).
- **PII & Credentials**: Emails, JWT tokens, IP addresses (optional setting).

---

## 🔗 Related Notes
- [[Guardrails-Engine|Guardrails Engine]]
- [[Agent-Loop|Agent ReAct Loop]]
