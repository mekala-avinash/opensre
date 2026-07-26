---
aliases:
  - Troubleshooting and FAQ
  - Footgun Prevention
  - Common Mistakes
tags:
  - opensre/ops
  - opensre/faq
type: note
updated: 2026-07-26
---

# ⚠️ Troubleshooting & Footgun Prevention Guide

This guide details high-priority pitfalls, code anti-patterns, and security footguns to avoid when working on OpenSRE.

---

## 🚫 Critical Footguns & Solutions

### 1. Planning-Stage Fail-Closed Safeguard
- **Pitfall**: Introducing a planner denial, `mark_unhandled`, or `UNHANDLED:` convention in the interactive shell planner.
- **Rule**: Never deny a turn. See [[Action-Planner-Policy|Action Planner Policy]].

### 2. Information Exposure (CWE-209 / CodeQL `py/stack-trace-exposure`)
- **Pitfall**: Returning `str(exc)` or `traceback.format_exc()` to external HTTP responses or chat sinks (Slack/Telegram).
- **Rule**: Redact exceptions at the external sink boundary (`OutputSink.render_error`). Log full detail server-side only. See [[Telegram-and-Slack-Sinks|Telegram & Slack Sinks]].

### 3. Function-Local Lazy Import Hacks
- **Pitfall**: Attempting to clear cyclic import warnings by moving an import inside a function. CodeQL still counts function-local imports in cycles.
- **Rule**: Structurally break cycles by extracting shared types or constants to `config/constants/` or `core/state/`. See [[Dependency-Rules|Dependency Rules]].

### 4. Draft-07 JSON Schema Failures
- **Pitfall**: Defining union types like `"type": ["object", "null"]` in tool input schemas. While valid in loose JSON schemas, certain LLM provider APIs reject them.
- **Rule**: Use explicit optional fields without type arrays. See [[Tool-Framework|Tool Framework Primitives]].

### 5. Mintlify Docs Navigation Disconnect
- **Pitfall**: Adding an `.mdx` file under `docs/` without registering it in `docs/docs.json`.
- **Rule**: Always add new page entries to `docs/docs.json` so they appear in the site sidebar navigation.

---

## 🔗 Related Notes
- [[Action-Planner-Policy|Action Planner Policy]]
- [[Telegram-and-Slack-Sinks|Telegram & Slack Sinks]]
- [[Dependency-Rules|Dependency Invariants]]
- [[CI-CD-and-Testing|CI/CD Parity & Testing]]
