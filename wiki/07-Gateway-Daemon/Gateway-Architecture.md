---
aliases:
  - Gateway Architecture
  - Gateway Daemon
  - OpenSRE Gateway
tags:
  - opensre/gateway
type: note
updated: 2026-07-26
---

# 📡 Gateway Daemon Architecture

The `gateway/` package houses the long-running daemon that listens for continuous inbound chat events from Slack, Telegram, and webhooks.

---

## 🏗️ Gateway Structure

```mermaid
flowchart TD
    subgraph Inbound["Inbound Chat & HTTP Streams"]
        TG["gateway/telegram (Telegram Bot)"]
        SL["gateway/slack (Slack Events)"]
        HTTP["gateway/http/webapp.py (Health WebApp)"]
    end

    subgraph CoreDaemon["Gateway Core Engine"]
        SESS["gateway/session (Session Lifecycle)"]
        STOR["gateway/storage (Persistent SQLite/Vault)"]
    end

    subgraph Dispatch["Capability Execution"]
        Runtime["tools + core Capability Layer"]
    end

    Inbound --> SESS
    SESS --> STOR
    SESS --> Dispatch
```

---

## 🔑 Key Responsibilities

1. **Independent Tier-1 Peer**: Serves as a peer to `surfaces/`. Never imports `surfaces/`.
2. **Health WebApp (`gateway/http/webapp.py`)**: FastAPI health check server running on container deployment.
3. **Session Persistence**: Maintains conversation history and active investigation context per chat channel.

---

## 🔗 Related Notes
- [[Telegram-and-Slack-Sinks|Telegram & Slack Output Sinks]]
- [[Session-and-Storage|Session State & Vault Storage]]
- [[Layer-Stack|Layer Stack Architecture]]
