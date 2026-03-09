# RAG CLI - Semantic Search & Document Retrieval for GTMA

🚀 **The fastest path from documents to semantic search.**

A powerful CLI tool for building RAG (Retrieval-Augmented Generation) pipelines. Chunk files, generate embeddings, store in MongoDB Vector Database, and query with intelligent retrieval.

---

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

## 🚀 Quick Start

### 1. Get Your API Keys
- Get a free API key from your embedding provider
- Configure your vector database credentials

### 2. Install
```bash
# Using curl
curl -fsSL https://your-installer-url.com/install.sh | sh

# Or using npm/pip (choose based on your implementation)
npm install -g rag-cli
# or
pip install rag-cli
```

### 3. Initialize & Test
```bash
rag quickstart
```
This launches an interactive tutorial to build your first RAG pipeline in 2 minutes!

### 4. 5-Minute RAG Pipeline
```bash
# 1. Configure your setup
rag config init

# 2. Chunk your documents
rag chunk --input documents/ --method semantic --output chunks.json

# 3. Generate embeddings
rag embed --input chunks.json --provider voyage-ai --model voyage-3

# 4. Store in vector database
rag store --input embeddings.json --database mongodb-atlas

# 5. Query!
rag query "What is RAG?" --top-k 5 --rerank
```

---

## 📖 Usage Options

### **CLI** (Terminal)
22+ commands covering the entire RAG workflow:
```bash
rag chunk      # Split documents into chunks
rag embed      # Generate embeddings
rag store      # Save to vector database
rag query      # Semantic search with optional reranking
rag rerank     # Two-stage retrieval with reranking
rag benchmark  # Compare embedding models
rag ingest     # Bulk import documents
```

### **Web Playground** 🌐
- Interactive interface with 7+ tabs
- Real-time testing and visualization
- Workflow templates and presets
- No installation required

---

## 💻 Installation

### Option 1: Automatic Install
```bash
curl -fsSL https://your-installer.com/install.sh | sh
```

### Option 2: Manual Install
```bash
# Clone the repository
git clone https://github.com/yourusername/rag-cli.git
cd rag-cli

# Install dependencies
npm install
# or
pip install -r requirements.txt

# Link globally
npm link
# or
pip install -e .
```

### Option 3: Docker
```bash
docker pull your-registry/rag-cli:latest
docker run -it your-registry/rag-cli:latest rag --help
```

---

## ⚙️ Configuration

Initialize your configuration:
```bash
rag config init
```

This creates a `~/.rag/config.yml` file:
```yaml
embeddings:
  provider: voyage-ai
  model: voyage-3
  api_key: ${VOYAGE_AI_API_KEY}

vector_db:
  type: mongodb-atlas
  connection_string: ${MONGODB_URI}
  index_name: documents

chunking:
  method: semantic
  chunk_size: 512
  overlap: 50

reranking:
  enabled: true
  model: rerank-2.5
```

---

## 🎯 Commands

### Chunking
```bash
# Fixed-size chunks
rag chunk --input docs/ --method fixed --chunk-size 512

# Semantic-aware chunking
rag chunk --input docs/ --method semantic

# Custom Python function
rag chunk --input docs/ --method custom --function my_chunker.py
```

### Embeddings
```bash
# Generate embeddings
rag embed --input chunks.json --provider voyage-ai --model voyage-3

# Use lite model for cost savings
rag embed --input chunks.json --model voyage-lite
```

### Storage
```bash
# Store in vector database
rag store --input embeddings.json --database mongodb-atlas

# Batch import
rag ingest --directory documents/ --batch-size 100
```

### Search & Retrieval
```bash
# Simple semantic search
rag query "machine learning basics"

# With reranking (two-stage retrieval)
rag query "machine learning basics" --rerank --top-k 5

# Hybrid search
rag query "machine learning" --hybrid --bm25-weight 0.3 --vector-weight 0.7
```

### Benchmarking
```bash
# Compare embedding models
rag benchmark --models voyage-3,openai,cohere --dataset test-data.csv

# Evaluate reranking quality
rag benchmark --rerankers rerank-2.5,cohere-rerank --metrics mrr,ndcg
```

---

## 🔀 Chunking Strategies

| Method | Best For | Overhead |
|--------|----------|----------|
| **Fixed** | Structured documents | Low |
| **Sliding Window** | Long sequences | Medium |
| **Semantic** | Context preservation | High |
| **Recursive** | Hierarchical documents | Medium |
| **Custom** | Specific use cases | Varies |

---

## 📚 Examples

### Example 1: Semantic Search on Local Documents
```bash
# Setup
rag config init --provider voyage-ai --db mongodb-atlas

# Ingest documents
rag ingest --directory ./my_docs --recursive

# Query
rag query "How to use RAG?" --top-k 3 --rerank
```

### Example 2: Compare Embedding Models
```bash
# Benchmark different models
rag benchmark \
  --models voyage-3,voyage-lite,openai \
  --test-queries queries.csv \
  --metrics accuracy,cost,speed
```

### Example 3: Custom Chunking Pipeline
```bash
# Use custom chunking function
rag chunk \
  --input documents.pdf \
  --method custom \
  --function ./my_chunker.js \
  --output chunks.json
```

---

## 📊 Benchmarking

Evaluate your RAG pipeline:
```bash
rag benchmark \
  --ground-truth evaluation_set.csv \
  --metrics mrr,ndcg,map \
  --output benchmark_results.json
```

Metrics included:
- **MRR**: Mean Reciprocal Rank
- **NDCG**: Normalized Discounted Cumulative Gain
- **MAP**: Mean Average Precision
- **Latency**: Query response time
- **Cost**: API call costs

---

## 🤝 Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🔗 Resources

- **Documentation**: [docs.rag-cli.com](https://docs.rag-cli.com)
- **GitHub**: [github.com/yourusername/rag-cli](https://github.com/yourusername/rag-cli)
- **Issues**: [Report bugs](https://github.com/yourusername/rag-cli/issues)
- **Discussions**: [Ask questions](https://github.com/yourusername/rag-cli/discussions)

---

## 💡 Common Questions

**Q: Do I need to know Python?**  
A: No! Everything works from the CLI. Python is optional for custom chunking functions.

**Q: Which embedding provider is best?**  
A: It depends on your use case. Try benchmarking with `rag benchmark` to compare.

**Q: How much does it cost?**  
A: Costs depend on your embedding provider and database. Use lite models for cost savings.

**Q: Can I use my own documents?**  
A: Yes! Supports PDF, TXT, MD, JSON, CSV, and more.

---

## ⭐ Show Your Support

If this project helped you, please give it a star! ⭐

---

**Made with ❤️ by [Your Name]**
