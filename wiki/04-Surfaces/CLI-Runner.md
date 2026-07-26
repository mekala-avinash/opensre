---
aliases:
  - CLI Runner
  - CLI Commands
  - Onboarding Wizard
tags:
  - opensre/surfaces
  - opensre/cli
type: note
updated: 2026-07-26
---

# 💻 CLI Runner & Setup Wizard

The CLI surface (`surfaces/cli/`) provides command-line execution for investigations, integration management, and interactive setup.

---

## ⚡ Primary CLI Commands

```bash
# Launch full autonomous incident investigation
uv run opensre investigate --alert ALERT_ID

# Run interactive setup wizard for integrations and providers
uv run opensre setup

# Verify configured vendor integrations
uv run opensre verify
```

---

## 🧙 Onboarding Wizard (`surfaces/cli/wizard/`)

The onboarding wizard handles step-by-step setup of LLM credentials, observability integrations, and local environment variables. Modular provider setup code resides under `surfaces/cli/wizard/<provider>.py`.

---

## 🔗 Related Notes
- [[Interactive-REPL|Interactive REPL Terminal]]
- [[Vendor-Integrations|Vendor Integrations]]
- [[Setup-and-Installation|Setup & Installation]]
