---
aliases:
  - Adding New Tools and Integrations
  - Adding Integrations
  - Definition of Done
tags:
  - opensre/ops
  - opensre/contributing
type: note
updated: 2026-07-26
---

# 🚀 Guide: Adding Tools & Vendor Integrations

Follow this step-by-step definition of done when adding a new tool or integration to OpenSRE.

> [!note] Policy Reference
> See [docs/adding-tools-and-integrations.md](file:///Users/amekala/Desktop/opensre/docs/adding-tools-and-integrations.md).

---

## 📝 Step-by-Step Workflow

```mermaid
flowchart TD
    S1["1. Create Integration Package\nintegrations/<vendor>/"] --> S2["2. Implement Credential Normalization & Verifier\nverifier.py"]
    S2 --> S3["3. Implement Tools\nBaseTool or @tool"]
    S3 --> S4["4. Register Tool & Config Model\nintegrations/catalog.py"]
    S4 --> S5["5. Write Unit & Integration Tests\ntests/"]
    S5 --> S6["6. Add Documentation\ndocs/<vendor>.mdx"]
    S6 --> S7["7. Run Verification Battery\nmake verify"]
```

---

## 🎯 Definition of Done Checklist

- [ ] `integrations/<vendor>/client.py` implements clean API interaction.
- [ ] `integrations/<vendor>/verifier.py` provides health check.
- [ ] Tool placement complies with [[Tool-Placement-Policy|Tool Placement Policy]].
- [ ] Draft-07 JSON schemas are validated.
- [ ] `make verify` and `make check-imports` pass cleanly.

---

## 🔗 Related Notes
- [[Tool-Placement-Policy|Tool Placement Policy]]
- [[Vendor-Integrations|Vendor Integration Architecture]]
- [[CI-CD-and-Testing|CI/CD Parity & Testing]]
