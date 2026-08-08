# Fashion Forward Hub — RAG Chatbot

Two notebooks building and improving a Retrieval-Augmented Generation (RAG) chatbot for a fictional e-commerce company, "Fashion Forward Hub." Built as coursework for a RAG-focused course, using [Weaviate](https://weaviate.io/) as the vector database.

## Contents

### `notebooks/C1M4_Assignment.ipynb` — Developing a RAG-based Chatbot
Builds a more sophisticated RAG system on top of a products + FAQ knowledge base:
- **LLM routing** — classify each incoming query (FAQ vs. product-related) and route it to the right handler
- **FAQ answering** — retrieval + generation over the FAQ database
- **Product search & recommendations** — retrieval + generation over the product catalog

### `notebooks/C1M5_Assignment.ipynb` — Improving a RAG System
Takes the chatbot from M4 and focuses on making it production-ready:
- **Cost measurement** — estimating the token/API cost of running the chatbot at scale
- **Prompt improvement** — tightening prompts for latency and quality trade-offs
- **Tracing** — instrumenting the pipeline with [Arize Phoenix](https://phoenix.arize.com/) for observability

## Requirements

- Python 3.10+
- `weaviate-client`
- An LLM API key (e.g. OpenAI) and a Weaviate instance (local or cloud)

See `requirements.txt` for the full dependency list.

## Setup

```bash
pip install -r requirements.txt
```

Set the following environment variables before running the notebooks (do **not** hardcode credentials in the notebook):

```bash
export OPENAI_API_KEY="your-key-here"
export WEAVIATE_URL="your-weaviate-endpoint"
export WEAVIATE_API_KEY="your-weaviate-key"
```

## Notes

These notebooks were completed as graded programming assignments for a course on building RAG systems. They're shared here as a personal portfolio/learning record.
