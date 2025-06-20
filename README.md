# LangChain RAG AI Chatbot

This repository implements a Retrieval-Augmented Generation (RAG) chatbot using LangChain, OpenAI's embedding API, and Chroma as a vector store. It demonstrates a basic pipeline for loading source documents, generating embeddings, storing them in a vector database, and querying for contextual answers using natural language.

## Project Overview

The project is built to showcase:

- Document chunking and preprocessing
- Vector embedding using OpenAI's `text-embedding-3-small` model
- Local persistence using Chroma vector store
- Querying stored data with natural language using LangChain

This serves as a foundational architecture for building custom AI chat interfaces over private datasets.

## Prerequisites

- Python 3.10+
- OpenAI API key with embedding access
- pip and virtualenv (recommended)

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/pixegami/langchain-rag-tutorial.git
cd langchain-rag-tutorial
```

### 2. Create a virtual environment

```bash
python -m venv .venv
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # macOS/Linux
```

### 3. Install dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

> Note: Ensure `openai>=1.30.1` is installed to avoid known client compatibility issues.

### 4. Configure the OpenAI API Key

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your-openai-api-key
```

Alternatively, export it in your environment:

```bash
# Windows PowerShell
$Env:OPENAI_API_KEY="your-openai-api-key"

# macOS/Linux
export OPENAI_API_KEY="your-openai-api-key"
```

## Usage

### Step 1: Build the vector store

Run the database creation script to process and embed your source documents:

```bash
python create_database.py
```

This will:

- Load documents from `data/books/`
- Split them into semantically meaningful chunks
- Create embeddings using OpenAI
- Persist them to the `chroma/` directory

### Step 2: Query the database

Use natural language to query your documents:

```bash
python query_data.py "What does the White Rabbit do?"
```

The script returns relevant answers based on vector similarity search against the embedded corpus.

## File Structure

```
.
├── create_database.py       # Document ingestion and embedding
├── query_data.py            # Query interface
├── requirements.txt         # Dependency definitions
├── .env                     # Environment variables (not committed)
└── data/
    └── psychology_explained.md
```

## Extending the Project

- Replace or augment documents in the `data/` folder to adapt this chatbot to your own data.
- Consider swapping the embedding provider for an open-source alternative (e.g., HuggingFace Transformers).
