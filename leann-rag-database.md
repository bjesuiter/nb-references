---
title: "LEANN - World's Smallest RAG Vector Database"
anchor: "97% storage savings, local and private RAG database from Berkeley Sky Lab"
tags: [rag, vector-database, local-ai, leann, berkeley, privacy, semantic-search]
description: "LEANN is an innovative local vector database achieving 97% storage savings while maintaining search quality"
source_url: "https://github.com/yichuan-w/LEANN"
---

## Reference

### Summary
LEANN (Low-Storage Vector Index) is a groundbreaking RAG vector database from Berkeley Sky Computing Lab that achieves **97% storage savings** compared to traditional solutions like FAISS.

### Key Features
- **🔒 Privacy-first**: 100% local, no cloud, no data leaves your device
- **💾 97% smaller storage**: 60M text chunks in 6GB vs 201GB
- **⚡ Fast**: Under 2 seconds for 90% top-3 recall on real-world QA
- **🌍 RAG on Everything**:
  - Documents (PDF, TXT, MD)
  - Apple Mail / Gmail
  - Browser history (Chrome)
  - WeChat, iMessage
  - ChatGPT / Claude conversations
  - Slack, Twitter (via MCP)
  - Codebases (Claude Code integration)

### Storage Comparison
| Data Type | Traditional (FAISS) | LEANN | Savings |
|-----------|---------------------|-------|---------|
| Wiki (60M chunks) | 201 GB | 6 GB | 97% |
| Chat (400K) | 1.8 GB | 64 MB | 97% |
| Email (780K) | 2.4 GB | 79 MB | 97% |
| Browser (38K) | 130 MB | 6.4 MB | 95% |

### Installation
```bash
# Install uv first
curl -LsSf https://astral.sh/uv/install.sh | sh

# Clone and install
git clone https://github.com/yichuan-w/LEANN.git leann
cd leann
uv venv && source .venv/bin/activate
uv pip install leann
```

### Quick Start
```python
from leann import LeannBuilder, LeannSearcher

# Build index
builder = LeannBuilder(backend_name="hnsw")
builder.add_text("Your text here")
builder.build_index("my-index.leann")

# Search
searcher = LeannSearcher("my-index.leann")
results = searcher.search("query", top_k=5)
```

### CLI Usage
```bash
# Build from documents
leann build my-docs --docs ./your_documents

# Search
leann search my-docs "machine learning concepts"

# Interactive chat
leann ask my-docs --interactive
```

### Claude Code Integration
```bash
# Install globally
uv tool install leann-core --with leann

# Add as MCP server for Claude Code
claude mcp add --scope user leann-server -- leann_mcp
```

### Why LEANN
- Graph-based selective recomputation (only compute embeddings when needed)
- HNSW and DiskANN backends
- MCP support for live data integration
- AST-aware code chunking for programming tasks
- MIT licensed, open source

### Resources
- **GitHub**: https://github.com/yichuan-w/LEANN
- **Paper**: https://arxiv.org/abs/2506.08276
- **Docs**: https://docs.usebruno.com (shared docs)
- **Berkeley Sky Lab**: https://sky.cs.berkeley.edu/

### Use Cases
- Personal AI assistant with semantic search
- Search email/browser history locally
- Claude Code integration for code search
- Index documents, chats, conversations
- Any private RAG application
