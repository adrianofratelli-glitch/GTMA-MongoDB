# RAG CLI - Semantic Search & Document Retrieval for GTMA

🚀 **The fastest path from documents to semantic search.**

A powerful CLI tool for building RAG (Retrieval-Augmented Generation) pipelines. Chunk files, generate embeddings, store in MongoDB Vector Database, and query with intelligent retrieval.

---

# Why VoyageAI?

Voyage AI provides state-of-the-art embedding models with the best quality-to-cost ratio in the industry. Here's why developers choose Voyage AI:

Advantage	What It Means
🎯 #1 on RTEB	Voyage 4 ranks first on retrieval benchmarks, outperforming OpenAI, Cohere, and other providers
💰 Up to 83% Cost Savings	Asymmetric retrieval: embed docs with voyage-4-lite, query with voyage-4-large, same quality, fraction of the cost
🔗 Shared Embedding Space	All Voyage 4 models produce compatible embeddings, so you can mix and match for optimal cost-quality tradeoffs
🏢 Domain-Specific Models	Specialized models for code, finance, law, and multilingual content that beat general-purpose alternatives
⚡ Two-Stage Retrieval	Rerank-2.5 boosts search precision by re-scoring candidates with a powerful cross-encoder

### Get started
```bash
# Get a free API key at https://dash.voyageai.com
vai quickstart    # Interactive tutorial — zero to semantic search in 2 minutes
```

## ✨ Features

- **🔄 End-to-End RAG Pipeline**: Ingest → Embed → Store → Query in minutes
- **📚 Multiple Chunking Methods**: Fixed size, sliding window, semantic-aware, and custom strategies
- **🤖 Embedding Integration**: Support for multiple embedding providers (OpenAI, Voyage AI, Hugging Face, etc.)
- **💾 Vector Database Support**: MongoDB Atlas Vector Search
- **🔍 Two-Stage Retrieval**: Semantic search + intelligent reranking for top precision
- **🎯 No Python Required**: Pure CLI - everything from the terminal
- **📊 Model Benchmarking**: Compare embeddings models performance
- **🎨 Web Playground**: Interactive UI for testing and exploration

---

# CLI - Quick Start

## Install
```bash

# Via npm
npm install -g voyageai-cli
```
# RAG Pipeline
Folder of documents to a searchable vector database:

```bash
# Set credentials
export VOYAGE_API_KEY="API-KEY"
export MONGODB_URI="mongodb+srv://<password>:Arianne1305@getnet.r6w6ng.mongodb.net/"

# Initialize project
vai init --yes

# Chunk → embed → store (one command)
vai pipeline ./voyage/ --db GTM --collection GTMA --create-index

# Search with two-stage retrieval
vai query "How do I configure replica sets?" --db GTM --collection GTMA
```
That's it. Documents chunked, embedded with voyage-4-large, stored in Atlas with metadata, vector index created, and searchable with reranking.

# Project Config

Stop typing --db GTM --collection GTMA on every command:

```bash
vai init
```

Creates .vai.json with your defaults — model, database, collection, chunking strategy. Every command reads it automatically. CLI flags override when needed.

```bash
{
  "model": "voyage-4-large",
  "db": "myapp",
  "collection": "knowledge",
  "field": "embedding",
  "dimensions": 1024,
  "chunk": {
    "strategy": "recursive",
    "size": 512,
    "overlap": 50
  }
}
```
