---
aliases:
  - Integrations Catalog
  - Vendor Catalog
tags:
  - opensre/integrations
  - opensre/catalog
type: note
updated: 2026-07-26
---

# 🔌 Integrations Catalog

OpenSRE features an extensive catalog (`integrations/catalog.py`) supporting dozens of cloud providers, APM vendors, log engines, databases, and alerting platforms.

---

## 📋 Supported Integrations Index

### Observability & APM
- **Datadog**: `integrations/datadog` (Metrics, APM traces, monitors, logs)
- **Grafana / Loki / Tempo**: `integrations/grafana`, `integrations/tempo`
- **Sentry**: `integrations/sentry`, `integrations/sentry_mcp`
- **Honeycomb**: `integrations/honeycomb`
- **Coralogix**: `integrations/coralogix`
- **SigNoz**: `integrations/signoz`
- **Better Stack**: `integrations/betterstack`
- **OpenObserve**: `integrations/openobserve`
- **VictoriaLogs**: `integrations/victoria_logs`
- **PostHog**: `integrations/posthog`

### Infrastructure & Cloud Providers
- **AWS**: `integrations/aws` (EC2, EKS, CloudWatch, CloudTrail, RDS, S3, Lambda, ELB)
- **Azure**: `integrations/azure` (Azure Monitor, Azure SQL)
- **Kubernetes / Helm**: `integrations/kubernetes`, `integrations/helm`
- **ElasticSearch / OpenSearch**: `integrations/elasticsearch`, `integrations/opensearch`
- **ClickHouse**: `integrations/clickhouse`

### Databases & Queues
- **PostgreSQL / MySQL / MariaDB**: `integrations/postgresql`, `integrations/mysql`, `integrations/mariadb`
- **Redis / MongoDB / Supabase**: `integrations/redis`, `integrations/mongodb`, `integrations/supabase`
- **Snowflake**: `integrations/snowflake`
- **Kafka / RabbitMQ**: `integrations/kafka`, `integrations/rabbitmq`

### Incident & Alerting Platforms
- **PagerDuty / Opsgenie**: `integrations/pagerduty`, `integrations/opsgenie`
- **Incident.io / ServiceNow**: `integrations/incident_io`, `integrations/servicenow`
- **Alertmanager**: `integrations/alertmanager`

### CI/CD & Version Control
- **GitHub / GitLab / Bitbucket**: `integrations/github`, `integrations/gitlab`, `integrations/bitbucket`
- **ArgoCD / Airflow / Dagster / Prefect / Temporal**: `integrations/argocd`, `integrations/airflow`, `integrations/dagster`, `integrations/prefect`, `integrations/temporal`
- **Jenkins**: `integrations/jenkins`

---

## 🔗 Related Notes
- [[Vendor-Integrations|Vendor Integration Architecture]]
- [[Adding-New-Tools-and-Integrations|Adding Tools & Integrations Guide]]
