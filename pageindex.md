---
title: PageIndex - Vectorless Reasoning-based RAG
anchor: Document indexing framework without vector DB or chunking, uses hierarchical tree structure and LLM reasoning for retrieval
tags: [rag, document-analysis, llm, vectorless, reasoning, retrieval]
description: PageIndex transforms PDFs into semantic tree structures for reasoning-based RAG without vectors or chunking
source_url: https://github.com/VectifyAI/PageIndex
---

## Summary

**PageIndex** is a vectorless, reasoning-based RAG system that builds a hierarchical tree index (like a Table of Contents) from long documents. Instead of vector similarity search, it uses LLM reasoning to navigate and extract relevant sections.

### Core Features
- **No Vector DB** - Uses document structure + LLM reasoning
- **No Chunking** - Natural sections, not artificial chunks
- **Human-like Retrieval** - Simulates expert document navigation
- **Explainable** - Traceable reasoning with page/section references

### Performance
- **98.7% accuracy** on FinanceBench benchmark (Mafin 2.5 system)
- Significantly outperforms traditional vector-based RAG

### Integration Options
1. **Self-host** - Open-source repo
2. **Cloud** - https://chat.pageindex.ai
3. **MCP** - https://pageindex.ai/mcp
4. **API** - https://docs.pageindex.ai/quickstart (beta)

### Resources
- [Cookbooks](https://docs.pageindex.ai/cookbook/vectorless-rag-pageindex)
- [Introduction Blog](https://pageindex.ai/blog/pageindex-intro)
- [MCP Setup Guide](https://pageindex.ai/mcp#quick-setup)

### Quick CLI Usage
```bash
pip install -r requirements.txt
# Set CHATGPT_API_KEY in .env
python3 run_pageindex.py --pdf_path /path/to/document.pdf
```
