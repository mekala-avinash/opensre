---
aliases:
  - Investigation Stages
  - The 6 Stages
tags:
  - opensre/investigation
  - opensre/stages
type: note
updated: 2026-07-26
---

# 🪜 Breakdown of the 6 Investigation Stages

Each stage in `tools/investigation/stages/` has a distinct purpose, specific tool subset, and strict output requirements.

---

## 📋 Stage Details

### Stage 1: Triage (`stage_1_triage.py`)
- **Goal**: Parse the initial alert or user report, identify affected services, determine severity, and establish the time window.
- **Tools**: Alert manager lookup, PagerDuty/Opsgenie fetch, service catalog query.

### Stage 2: Hypothesis Generation (`stage_2_hypothesis.py`)
- **Goal**: Formulate testable hypotheses (e.g. database pool exhaustion, bad deployment, network partition).
- **Output**: List of prioritized hypotheses stored in `InvestigationSlice.hypotheses`.

### Stage 3: Evidence Gathering (`stage_3_evidence.py`)
- **Goal**: Execute targeted telemetry queries to prove or disprove hypotheses.
- **Tools**: Datadog metrics, Grafana Loki logs, Sentry error traces, Kubernetes pod stats.

### Stage 4: Root Cause Analysis (`stage_4_rca.py`)
- **Goal**: Correlate collected evidence to isolate the definitive root cause.
- **Output**: Structured `RootCauseSummary` with confidence score and evidence citations.

### Stage 5: Remediation Planning (`stage_5_remediation.py`)
- **Goal**: Propose actionable mitigation steps (e.g. rollback deployment, scale replicas, restart service).
- **Guardrails**: Action plan submitted for guardrail verification before presenting to user.

### Stage 6: Incident Reporting (`stage_6_reporting.py`)
- **Goal**: Render comprehensive post-mortem report for human engineers and incident management tools.

---

## 🔗 Related Notes
- [[Pipeline-Lifecycle|Investigation Pipeline Lifecycle]]
- [[Evidence-Gathering|Evidence & Signal Correlation]]
- [[Reporting|Incident Reporting]]
