---
aliases:
  - Setup and Installation
  - Development Setup
  - Getting Started
tags:
  - opensre/ops
  - opensre/setup
type: note
updated: 2026-07-26
---

# 🛠️ Machine Setup & Installation

Get OpenSRE set up for local development across macOS, Linux, or Windows.

> [!note] Reference Files
> See [SETUP.md](file:///Users/amekala/Desktop/opensre/SETUP.md) and [Makefile](file:///Users/amekala/Desktop/opensre/Makefile).

---

## ⚡ Quick Start Installation

```bash
# 1. Clone repository
git clone https://github.com/Tracer-Cloud/opensre.git
cd opensre

# 2. Build environment via Makefile (installs uv dependencies and editable package)
make install

# 3. Verify opensre CLI execution
uv run opensre --help
```

---

## 🐍 Python Execution Rules

> [!important] Command Rule
> Always execute commands using **`uv run opensre ...`** or **`uv run python ...`** from the repository root while developing. This guarantees that your local checkout is used instead of any global `opensre` installed on your `PATH`.

---

## 🔗 Related Notes
- [[CLI-Runner|CLI Runner]]
- [[CI-CD-and-Testing|CI/CD & Testing Guide]]
