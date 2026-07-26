---
aliases:
  - Evidence Gathering
  - Signal Correlation
tags:
  - opensre/investigation
  - opensre/evidence
type: note
updated: 2026-07-26
---

# 🧬 Evidence & Signal Correlation

Evidence gathering collects and correlates telemetry signals from diverse observability sources into unified `EvidenceEntry` records stored in `AgentState.evidence`.

---

## 📊 Signal Classification Matrix

| Category | Typical Sources | Data Collected |
| :--- | :--- | :--- |
| **`logs`** | Grafana Loki, Datadog Logs, Hermes, ElasticSearch | Exception stack traces, error rate spikes |
| **`metrics`** | Prometheus, Datadog Metrics, CloudWatch | CPU, Memory, Latency (p95/p99), HTTP 5xx rates |
| **`traces`** | Sentry, Honeycomb, Tempo | Span bottlenecks, failing database queries |
| **`deploys`** | GitHub Actions, ArgoCD, Helm, Kubernetes | Recent deployment commits, image tag changes |

---

## 🔗 Related Notes
- [[Agent-State|Agent State & Evidence Models]]
- [[Investigation-Stages|Investigation Stages]]
- [[Hermes-Log-Pipeline|Hermes Log Pipeline]]
