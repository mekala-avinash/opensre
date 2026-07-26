---
aliases:
  - Dependency Rules
  - Import Rules
  - CI Import Checks
tags:
  - opensre/architecture
  - opensre/ci
type: note
updated: 2026-07-26
---

# 🚫 OpenSRE Dependency Rules & CI Compliance

To maintain a clean architectural boundary, OpenSRE enforces strict directional import rules using `.importlinter` and CI scripts (`make check-imports`).

> [!warning] Key Rule
> **Lower tiers must NEVER import higher tiers.** Circular dependencies and illegal cross-tier imports fail the CI build instantly.

---

## 📋 Dependency Matrix Summary

```
Tier 1: surfaces, gateway ──┐
                            ▼
Tier 2: tools ────────► integrations
           │                 │
           ▼                 ▼
Tier 3: core ◄──────────────► platform
           │                 │
           ▼                 ▼
Tier 4: config ◄─────────────┘
```

1. **`config`** must never import from any first-party package.
2. **`core` and `platform`** may only import from `config` (and from each other).
3. **`integrations`** may import `core`, `platform`, `config`, but must **never** import `tools`, `surfaces`, or `gateway`.
4. **`tools`** may import `integrations`, `core`, `platform`, `config`, but must **never** import `surfaces` or `gateway`.
5. **`surfaces` and `gateway`** may import everything below them, but must **never** import each other.

---

## 🛠️ CI Import Check Commands

To run import boundary validation locally:

```bash
make check-imports
# Or using uv directly:
uv run lint-imports --config .importlinter
```

> [!important] Avoiding Function-Local Import Hacks
> When dealing with CodeQL `py/cyclic-import` or `import-linter` failures:
> **Do NOT use function-local lazy imports.** CodeQL traces function-local imports as cycle dependencies. Break cycles structurally by placing shared types or constants in `config/constants/` or `core/state/`.

---

## 🔗 Related Notes
- [[Architecture-Overview|Architecture Overview]]
- [[Layer-Stack|Layer Stack Detail]]
- [[Naming-Conventions|Domain Naming & Glossary]]
