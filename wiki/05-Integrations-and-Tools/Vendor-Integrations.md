---
aliases:
  - Vendor Integrations
  - Integration Architecture
tags:
  - opensre/integrations
type: note
updated: 2026-07-26
---

# 🏢 Vendor Integration Architecture

Every vendor package under `integrations/<vendor>/` strictly adheres to a standardized structure for credential resolution, health verification, and client access.

---

## 📂 Standard Integration Layout

```
integrations/<vendor>/
├── __init__.py
├── client.py           # Vendor API HTTP client wrapper
├── verifier.py         # Credentials and connectivity check (verify())
├── config_models.py    # Pydantic configuration schema
└── tools/              # Vendor-specific agent tools
    └── <tool_name>.py
```

---

## ⚙️ Core Components

1. **`client.py`**: Handles authentication headers, rate limits, and API requests.
2. **`verifier.py`**: Executes a lightweight health check (e.g. `get_me` or `list_dashboards`) when `opensre verify` is run.
3. **`config_models.py`**: Validates environment variables and local credentials store.

---

## 🔗 Related Notes
- [[Integrations-Catalog|Integrations Catalog]]
- [[Adding-New-Tools-and-Integrations|Adding New Tools & Integrations Guide]]
