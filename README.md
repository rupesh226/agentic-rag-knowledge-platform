# 🤖 Agentic RAG Knowledge Platform

A production-oriented AI platform for intelligent question answering over private enterprise documents using **LangChain, LangGraph, RAG, and tool-enabled agent workflows**.

---

## 🚀 Overview

This project demonstrates how to build an **Agentic Retrieval-Augmented Generation (RAG) system** that enables users to:

- 📄 Ingest private documents (PDF, DOCX, TXT)
- 🧠 Convert documents into embeddings
- 🔍 Perform semantic search over a vector database
- 💬 Ask natural language questions
- 🤖 Use AI agents with tool-calling capabilities
- 📚 Get grounded answers with source references

---

## 🏗️ Architecture

                    ┌──────────────────────────┐
                    │        End User          │
                    │  Web UI / Chat Interface │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │      API / App Layer     │
                    │ FastAPI / Streamlit UI   │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │     LangChain Agent      │
                    │  Reasoning + Tool Use    │
                    └───────┬─────────┬────────┘
                            │         │
                ┌───────────┘         └─────────────┐
                ▼                                   ▼
     ┌──────────────────────┐            ┌──────────────────────┐
     │    RAG Retriever     │            │   Optional Tools     │
     │ similarity / hybrid  │            │ web, calculator,     │
     │ retrieval over docs  │            │ metadata lookup      │
     └──────────┬───────────┘            └──────────────────────┘
                │
                ▼
     ┌──────────────────────────────┐
     │       Vector Database        │
     │ Pinecone / Chroma / FAISS    │
     └──────────┬───────────────────┘
                │
                ▼
     ┌──────────────────────────────┐
     │ Embeddings + Document Index  │
     │ chunking, metadata, ids      │
     └──────────┬───────────────────┘
                │
                ▼
     ┌──────────────────────────────┐
     │  Document Ingestion Pipeline │
     │ PDF, DOCX, TXT, HTML, MD     │
     └──────────┬───────────────────┘
                │
                ▼
     ┌──────────────────────────────┐
     │ Private Document Repository  │
     │ local files / blob / S3      │
     └──────────────────────────────┘




### Key Components

- **LLM Layer**: OpenAI / Azure OpenAI / Ollama
- **Agent Layer**: LangChain + LangGraph
- **Retrieval Layer**: Vector DB (Chroma / Pinecone / Azure AI Search)
- **Ingestion Pipeline**: Document loaders + chunking + embeddings
- **Frontend**: Streamlit
- **Backend API**: FastAPI

---

## 🔄 System Flow

### 1. Document Ingestion
Documents → Loaders → Chunking → Embeddings → Vector DB



### 2. Query Processing
User Question → Agent → Retriever → Context → LLM → Answer + Sources



---

## 🧠 Features

### ✅ Core Features
- Document ingestion pipeline
- Chunking & preprocessing
- Vector search (semantic retrieval)
- Question answering over private data
- Source-aware responses (citations)

### ⚡ Advanced (Agentic AI)
- Tool-calling agent (LangChain)
- Multi-step reasoning
- External tool integration (search, APIs)
- Extensible architecture

---

## Setup

1. Install dependencies:
```bash
uv sync
```

2. Set environment variables:
```bash
OPENAI_API_KEY=your_openai_key
PINECONE_API_KEY=your_pinecone_key
INDEX_NAME=your_index_name
```

3. Run ingestion to populate the vector store:
```bash
python ingestion.py
```

4. Run the RAG pipeline:
```bash
python main.py
```

## Why LCEL?

The tutorial demonstrates two approaches to building RAG:

| Feature | Naive Approach | LCEL Approach |
|---------|----------------|---------------|
| Code style | Imperative | Declarative |
| Streaming | Manual implementation | Built-in `.stream()` |
| Async | Manual implementation | Built-in `.ainvoke()` |
| Composability | Limited | Pipe operator `\|` |
| Batch processing | Manual loops | Built-in `.batch()` |

## Technologies

- **LangChain** - Framework for building LLM applications
- **OpenAI** - Embeddings and chat completions
- **Pinecone** - Vector database for similarity search
- **Python** - 3.12+