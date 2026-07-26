---
aliases:
  - System Tools
  - Operational Tools
tags:
  - opensre/tools
  - opensre/system
type: note
updated: 2026-07-26
---

# 🛠️ System & Operational Tools

System tools (`tools/system/`) provide vendor-agnostic operational capabilities for monitoring, script execution, watchdog alerting, and SRE guidance.

---

## 📌 System Tools Index

### 1. Fleet Monitoring (`tools/system/fleet_monitoring/`)
- Aggregates health metrics across multi-cluster Kubernetes and cloud node instances.

### 2. WatchDog Alarm Engine (`tools/system/watch_dog/`)
- Dispatches per-threshold Telegram and Slack alarms with automatic alert cooldowns.

### 3. Python Execution Tool (`tools/system/python_execution_tool/`)
- Executes Python diagnostic scripts in a sandboxed local runtime environment.

### 4. SRE Guidance Tool (`tools/system/sre_guidance_tool/`)
- Provides site reliability engineering patterns, SLO/SLI guidance, and runbook suggestions.

---

## 🔗 Related Notes
- [[Tool-Placement-Policy|Tool Placement Guidelines]]
- [[Tool-Framework|Tool Framework Primitives]]
- [[Cross-Vendor-Tools|Cross-Vendor Tools]]
