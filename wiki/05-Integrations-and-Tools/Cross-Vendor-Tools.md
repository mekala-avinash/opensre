---
aliases:
  - Cross Vendor Tools
  - Multi Vendor Tools
tags:
  - opensre/tools
  - opensre/cross_vendor
type: note
updated: 2026-07-26
---

# 🔀 Cross-Vendor Capability Tools

Cross-vendor tools (`tools/cross_vendor/`) orchestrate complex SRE workflows spanning two or more vendor integrations.

---

## ⚡ Featured Tool: `fix_sentry_issue`

`tools/cross_vendor/fix_sentry_issue.py` automates the remediation workflow for Sentry exceptions:

```mermaid
sequenceDiagram
    participant Agent as Investigation Agent
    participant Sentry as integrations/sentry
    participant GitHub as integrations/github
    participant Code as tools/system/python_execution_tool

    Agent->>Sentry: Fetch issue stack trace & exception frequency
    Sentry-->>Agent: SentryIssuePayload
    Agent->>GitHub: Locate file, git blame, and repository commit
    GitHub-->>Agent: Source file content
    Agent->>Code: Run diagnostic fix verification
    Agent->>GitHub: Propose Pull Request with fix
```

---

## 🔗 Related Notes
- [[Tool-Placement-Policy|Tool Placement Guidelines]]
- [[Vendor-Integrations|Vendor Integrations]]
- [[System-Tools|System Tools]]
