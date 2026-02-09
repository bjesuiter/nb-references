---
title: Recursive Language Models (RLM) in ADK
anchor: Architecture for managing massive context (10M+ tokens) via recursive agent delegation
tags: [llm, architecture, recursive, context, adk, agent, google]
description: Article about RLM architecture for managing massive context via recursive agent delegation
source_url: https://medium.com/google-cloud/recursive-language-models-in-adk-d9dc736f0478
source_url_alt: https://discuss.google.dev/t/recursive-language-models-in-adk/323523
---

## My Reference

### Summary
Recursive Language Models (RLM) is an architecture proposed by Alex Zhang et al. at MIT (late 2025) that enables agents to handle extremely long context (10M+ tokens) by manipulating context in a code REPL and recursively delegating tasks to child agents.

### Key Concepts
- **Context Control:** Agent controls its own context via a Python REPL with pre-defined variables/functions
- **Recursive Delegation:** Agent invokes `rlm_agent(query, context)` to spawn child agents with identical architecture
- **Task Decomposition:** Splits complex tasks across multiple agents without burning reasoning tokens
- **Code Execution:** Writes Python code using context objects, executes, and iterates based on results

### Architecture Benefits
1. Scales to 10M+ tokens (far beyond standard context windows)
2. Solves "quadratic" problems like cross-referencing statements across large documents
3. Parallelism for enterprise use cases
4. Lazy file loading for distributed data sources

### OOLONG-Pairs Benchmark
- Tests ability to find contradictions across pairs of statements in long documents
- RLM scored 23/100, other agents scored 0

### ADK Implementation
- Google's Agent Development Kit (ADK) used to implement RLM in enterprise-ready format
- Required extending BaseAgent (LLMAgent was too limiting)
- Extensions: lazy file loading, parallelism, real-time UI visualization

### Links
- [Paper: arxiv.org/abs/2512.24601](https://arxiv.org/abs/2512.24601)
- [ADK Implementation: github.com/LiamConnell/adk-python](https://github.com/LiamConnell/adk-python/tree/main/contributing/samples/rlm)
- [Original RLM: github.com/alexzhang13/rlm](https://github.com/alexzhang13/rlm)
