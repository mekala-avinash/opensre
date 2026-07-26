---
aliases:
  - Layer Stack
  - Four Tier Architecture
tags:
  - opensre/architecture
  - opensre/layers
type: note
updated: 2026-07-26
---

# 📦 The OpenSRE Layer Stack

The OpenSRE framework is designed as a modular 4-tier stack. This separation guarantees that agent execution logic remain decoupled from user-facing surfaces and third-party vendor clients.

> [!note] Source File
> See [docs/ARCHITECTURE.md](file:///Users/amekala/Desktop/opensre/docs/ARCHITECTURE.md) for the exact specification.

---

## 🏔️ Tier 1 — External Interfaces

### `surfaces/`
Contains entry points for human interactions:
- **`surfaces/cli`**: The stateless `opensre <command>` CLI runner.
- **`surfaces/interactive_shell`**: The stateful REPL terminal UI.
- **`surfaces/slack_app`**: Interactive bot app for Slack workspaces.
- **`surfaces/shared`**: Cross-surface formatting and output helpers.

### `gateway/`
Standalone messaging gateway daemon handling long-running background channels:
- Telegram Bot sink (`gateway/telegram`)
- Slack RTM/Socket sink (`gateway/slack`)
- Session management (`gateway/session`) & persistent storage (`gateway/storage`).

---

## ⚙️ Tier 2 — Capability Layer

### `integrations/`
Provides user credential management, verification, and raw API client wrappers for external vendors:
- Per-vendor modules: `integrations/datadog`, `integrations/grafana`, `integrations/aws`, `integrations/kubernetes`, `integrations/sentry`, etc.
- Config store (`integrations/store.py`) & catalog registry (`integrations/catalog.py`).
- Hermes log pipeline (`integrations/hermes`).

### `tools/`
Contains agent-callable tool specifications:
- Framework base classes (`BaseTool`, `@tool` decorator in `core/tool_framework`).
- Tool registry (`tools/registry.py`, `tools/registry_discovery.py`).
- System tools (`tools/system/`): Fleet monitoring, Python execution, WatchDog.
- Cross-vendor tools (`tools/cross_vendor/`): Workflows spanning multiple integrations.
- Investigation composite capability (`tools/investigation/`).

---

## 🧠 Tier 3 — Runtime & Platform Services

### `core/`
Provider-agnostic AI agent execution runtime:
- ReAct loop execution engine (`core.agent.Agent`).
- Context budget and token compaction (`core/context_budget.py`).
- State envelope and investigation slices (`core/state/`).
- Tool decorator & framework (`core/tool_framework/`).
- Hosted LLM adapters (`core/llm/`).

### `platform/`
Infrastructure services supporting the agent:
- Guardrails evaluation engine (`platform/guardrails/`).
- Sensitive data masking (`platform/masking/`).
- Command sandbox execution (`platform/sandbox/`).
- Observability and analytics (`platform/observability/`, `platform/analytics/`).
- EC2 single-instance deployment (`platform/deployment/`).

---

## 🎨 Tier 4 — Configuration Leaf

### `config/`
Static leaf package supplying constants across the application:
- Domain static constants (`config/constants/`).
- Keyring credential loading (`config/llm_keyring.py`).
- Environment variable parser (`config/env_file.py`).
- REPL UI configuration (`config/repl_config.py`).

---

## 🔗 Related Notes
- [[Architecture-Overview|Architecture Overview]]
- [[Dependency-Rules|Dependency Rules & CI Validation]]
- [[Tool-Placement-Policy|Tool Placement Guidelines]]
