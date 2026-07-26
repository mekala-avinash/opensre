---
aliases:
  - Tool Placement Policy
  - Tool Placement
tags:
  - opensre/architecture
  - opensre/tools
type: note
updated: 2026-07-26
---

# 🛠️ OpenSRE Tool Placement Policy

Where should a new tool live? OpenSRE establishes clear decision rules for locating tool implementations across `integrations/<vendor>/tools/`, `tools/system/`, `tools/cross_vendor/`, or `surfaces/shared/`.

> [!note] Policy Reference
> See [docs/tool-placement-policy.md](file:///Users/amekala/Desktop/opensre/docs/tool-placement-policy.md) for official decision trees.

---

## 🌳 Placement Decision Matrix

```mermaid
flowchart TD
    Q1{"Is the tool specific to a single vendor?"}
    Q1 -- Yes --> VENDOR["integrations/<vendor>/tools/\ne.g. integrations/datadog/tools/"]
    Q1 -- No --> Q2{"Does it orchestrate logic across 2+ vendors?"}
    Q2 -- Yes --> CROSS["tools/cross_vendor/\ne.g. tools/cross_vendor/fix_sentry_issue.py"]
    Q2 -- No --> Q3{"Is it a pure system / runtime capability?"}
    Q3 -- Yes --> SYS["tools/system/\ne.g. tools/system/watch_dog/"]
    Q3 -- No --> SURFACE["surfaces/shared/\ne.g. REPL helper tools"]
```

---

## 📍 Tool Categories & Paths

### 1. Single-Vendor Tools (`integrations/<vendor>/tools/`)
- **Criteria**: Operates against a single vendor's API client (Datadog query, Sentry issue fetch, Grafana dashboard query, AWS EC2 describe).
- **Location**: `integrations/<vendor>/tools/<tool_name>.py`

### 2. Cross-Vendor Tools (`tools/cross_vendor/`)
- **Criteria**: Combines data or workflows across multiple independent vendor integrations.
- **Example**: `tools/cross_vendor/fix_sentry_issue.py` (reads Sentry error, inspects GitHub repository, executes fix).

### 3. System Tools (`tools/system/`)
- **Criteria**: Vendor-agnostic operational capabilities.
- **Examples**:
  - `tools/system/fleet_monitoring/` — Infrastructure health monitoring.
  - `tools/system/watch_dog/` — Background Telegram alarm dispatch.
  - `tools/system/sre_guidance_tool/` — SRE best practices guidance.

---

## 🔗 Related Notes
- [[Architecture-Overview|Architecture Overview]]
- [[Integrations-Catalog|Integrations Catalog]]
- [[Adding-New-Tools-and-Integrations|Adding New Tools & Integrations Guide]]
