---
title: Monty - Secure Python Interpreter in Rust for AI Agents
anchor: Minimal secure Python sandbox interpreter written in Rust for running LLM-generated code safely
tags: [python, rust, sandbox, security, ai-agents, pydantic, code-execution]
description: Monty is a minimal, secure Python interpreter in Rust for safely running AI agent code without container overhead
source_url: https://github.com/pydantic/monty
---

## Reference

### Summary
Monty is a minimal, secure Python interpreter written in Rust for AI agents. It avoids the cost/latency of full container sandboxes while providing safe code execution for LLM-generated Python code.

### Key Features

| Feature | Description |
|---------|-------------|
| **Zero filesystem access** | Completely blocked - all I/O via controlled external functions |
| **No env/network access** | Sandboxed by design |
| **Microsecond startup** | vs. hundreds of ms for containers |
| **Type checking included** | Full Python type hints with `ty` integrated |
| **Snapshot support** | Store/resume interpreter state to DB/files |
| **Cross-platform** | Python, JS/TS, and Rust APIs |

### Limitations (by design)

- No standard library (except: `sys`, `typing`, `asyncio`, `dataclasses`, `json`)
- No third-party libraries (no Pydantic, etc.)
- No class definitions (coming soon)
- No match statements (coming soon)

### Installation

```bash
uv add pydantic-monty
# or
pip install pydantic-monty
```

### Use Cases
- **Codegen agents** that need to run LLM-generated code safely
- **Programmatic tool calling** (Anthropic-style)
- **Smol agents** pattern (Hugging Face)

### Related Reading
- [Cloudflare Code Mode](https://blog.cloudflare.com/code-mode/)
- [Anthropic Programmatic Tool Calling](https://platform.claude.com/docs/en/agents-and-tools/tool-use/programmatic-tool-calling)
- [Anthropic Code Execution with MCP](https://www.anthropic.com/engineering/code-execution-with-mcp)
- [Hugging Face Smol Agents](https://github.com/huggingface/smolagents)

### Note
Monty will power `codemode` in Pydantic AI (coming soon).
