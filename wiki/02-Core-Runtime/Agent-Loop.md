---
aliases:
  - Agent Loop
  - Agent ReAct Loop
  - Think Call Observe Loop
tags:
  - opensre/core
  - opensre/agent
type: note
updated: 2026-07-26
---

# ⚡ Think-Call-Observe Agent Loop

The core execution engine of OpenSRE lives in `core/agent/`. It drives an autonomous **Reasoning & Action (ReAct)** loop that repeatedly prompts the configured LLM provider, executes selected tools, applies safety guardrails, updates state, and manages context token limits.

---

## 🔄 Agent Execution Cycle

```mermaid
sequenceDiagram
    autonumber
    participant User as Surface / Pipeline
    participant Agent as core.agent.Agent
    participant Budget as ContextBudgetManager
    participant LLM as Provider LLM Client
    participant Guard as Guardrails & Masking
    participant Tool as BaseTool / Registry

    User->>Agent: execute_turn(input_state)
    loop Until Turn Complete or Tool Cap Reached
        Agent->>Budget: check_and_compact(messages)
        Budget-->>Agent: compacted_messages
        Agent->>LLM: invoke(compacted_messages, tool_schemas)
        LLM-->>Agent: LLMResponse (thought + tool_calls)
        alt LLM requests tool execution
            Agent->>Guard: evaluate_guardrails(tool_call)
            Guard-->>Agent: status (ALLOW / DENY)
            Agent->>Tool: execute(params)
            Tool-->>Agent: tool_output
            Agent->>Guard: mask_sensitive_data(tool_output)
            Guard-->>Agent: sanitized_output
            Agent->>Agent: append_tool_result_to_state()
        else LLM returns final response
            Agent->>Agent: mark_turn_complete()
        end
    end
    Agent-->>User: updated_agent_state
```

---

## ⚙️ Key Agent Components

### 1. Loop Control (`core.agent.Agent`)
- Executes turns in an asynchronous loop (`async run_turn()`).
- Tracks turn counts and prevents infinite looping with stagnation breakers.
- Implements tool cap safeguards (default cap per investigation turn).

### 2. Guardrails & Masking Middleware
- **Guardrails**: Calls `platform/guardrails/` before any tool call is executed. If a tool call violates security policies (e.g. destructive commands without user confirmation), execution is blocked.
- **Masking**: Sanitizes tool execution outputs via `platform/masking/` to redact API keys, tokens, and PII before appending to message history.

---

## 🔗 Related Notes
- [[Context-Budget|Context Budget & Compaction]]
- [[Agent-State|Agent State Architecture]]
- [[Tool-Framework|Tool Framework Primitives]]
- [[Guardrails-Engine|Guardrails Engine]]
