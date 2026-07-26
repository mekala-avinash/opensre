---
aliases:
  - Tool Framework
  - BaseTool
  - Tool Decorator
tags:
  - opensre/core
  - opensre/tools
type: note
updated: 2026-07-26
---

# 🧰 Core Tool Framework & Primitives

Tools in OpenSRE are defined using `core/tool_framework/`. The framework provides both class-based (`BaseTool`) and function-based (`@tool`) primitives, schema validation, and standardized error handling.

---

## 🛠️ Defining Tools

### Method 1: `@tool` Decorator (Lightweight Functions)

```python
from core.tool_framework.tool_decorator import tool

@tool(
    name="get_pod_logs",
    description="Fetch container logs from a Kubernetes pod",
    source="kubernetes",
)
async def get_pod_logs(namespace: str, pod_name: str, tail_lines: int = 100) -> str:
    # Implementation...
    return logs
```

### Method 2: `BaseTool` Class (Rich Stateful Tools)

```python
from core.tool_framework.base import BaseTool

class DatadogQueryTool(BaseTool):
    name = "datadog_query_metrics"
    description = "Query timeseries metrics from Datadog"

    async def execute(self, query: str, from_time: int, to_time: int) -> dict:
        client = self.get_client()
        return await client.query(query, from_time, to_time)
```

---

## 🛡️ Tool Execution Principles

> [!important] Error Classification
> Tools should handle transient API failures cleanly and return descriptive error messages rather than letting unhandled exceptions crash the ReAct loop.

> [!warning] JSON Schema Strictness
> LLM providers require strict Draft-07 JSON Schemas. Avoid ambiguous union types like `["object", "null"]` in tool input schemas.

---

## 🔗 Related Notes
- [[Tool-Placement-Policy|Tool Placement Guidelines]]
- [[Adding-New-Tools-and-Integrations|Adding Tools & Integrations Guide]]
- [[System-Tools|System & Operational Tools]]
