# RAG-Based E-Commerce Support Chatbot

An end-to-end Retrieval-Augmented Generation (RAG) chatbot for an e-commerce use case, covering both the initial build and a subsequent optimization pass focused on cost, latency, and observability. Built on [Weaviate](https://weaviate.io/) as the vector database, with a small Flask service layer and OpenTelemetry-based tracing via [Arize Phoenix](https://phoenix.arize.com/).

## What it does

The chatbot answers two distinct kinds of customer queries against a real knowledge base (product catalog + FAQ):

- **Query routing** — an LLM-based router classifies each incoming message (FAQ vs. product search) and dispatches it to the appropriate retrieval pipeline, rather than using a single one-size-fits-all prompt.
- **FAQ retrieval & generation** — semantic search over an FAQ collection in Weaviate, with the retrieved context grounding the LLM's answer.
- **Product search & recommendations** — structured filter extraction from natural-language queries (e.g. category, color, use-case) combined with vector search, so the bot can answer things like "do you have a lightweight jacket for hiking" without exact keyword matches.
- **Cost & performance optimization** — measuring per-query token cost, tightening prompts to cut latency and cost without degrading answer quality, and instrumenting the whole pipeline with distributed tracing to see where time and tokens are actually being spent.

## Project structure

```
notebooks/
├── C1M4_Assignment.ipynb   # Build: routing, FAQ RAG, product RAG
└── C1M5_Assignment.ipynb   # Optimize: cost analysis, prompt tuning, tracing
```

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

## Background

This project was originally developed as part of a course on building production RAG systems, then adapted here as a portfolio piece. The two notebooks mirror a realistic project arc: get a working RAG pipeline live first, then go back and make it fast, cheap, and observable enough to actually run in production.
