---
aliases:
  - Observability and Analytics
  - Platform Analytics
  - Harness Ports
tags:
  - opensre/platform
  - opensre/observability
type: note
updated: 2026-07-26
---

# 📊 Platform Observability, Analytics & Harness Ports

OpenSRE provides telemetry collection, execution event logging, and harness interface ports (`platform/observability/`, `platform/analytics/`, `platform/harness_ports.py`).

---

## 🔌 Harness Ports Architecture (`platform/harness_ports.py`)

`platform/harness_ports.py` defines the abstract interface ports connecting platform runtime services to surfaces and agent harnesses:

- **Integration Resolution Port**: Resolves active vendor integration configurations.
- **Tool Registry Port**: Exposes runtime tool discovery and schemas.
- **Investigation Port**: Entrypoint for launching and managing investigation sessions.

> [!note] Implementation Adapter
> Real implementations are wired at startup via `integrations/harness_adapters.py` and `tools/harness_adapters.py` through `install_harness_ports()`.

---

## 🔗 Related Notes
- [[Architecture-Overview|Architecture Overview]]
- [[Agent-Loop|Core Agent Loop]]
