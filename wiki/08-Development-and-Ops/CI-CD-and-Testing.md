---
aliases:
  - CI CD and Testing
  - Mandatory CI Checklist
  - Testing Guide
tags:
  - opensre/ops
  - opensre/ci
type: note
updated: 2026-07-26
---

# ✅ CI/CD Parity & Pre-Push Quality Checklist

Every pull request in OpenSRE must pass linting, formatting, typechecking, import boundary validation, and test suites.

> [!important] Mandatory Checklist
> See [CI.md](file:///Users/amekala/Desktop/opensre/CI.md) for the pre-push requirements.

---

## 🛠️ Complete Verification Commands

Run the canonical local automation targets prior to pushing:

```bash
# 1. Format code with Ruff
make format

# 2. Run Ruff linter
make lint

# 3. Perform Mypy type checks
make typecheck

# 4. Validate tier layer import boundaries
make check-imports

# 5. Run full test suite
make test

# 6. Execute complete verification battery
make verify
```

---

## 📝 Pull Request Guidelines

When opening a PR, fill out the [PR template](file:///Users/amekala/Desktop/opensre/.github/PULL_REQUEST_TEMPLATE.md) including the mandatory AI-usage disclosure section.

---

## 🔗 Related Notes
- [[Dependency-Rules|Dependency Invariants]]
- [[Adding-New-Tools-and-Integrations|Adding Tools & Integrations Guide]]
