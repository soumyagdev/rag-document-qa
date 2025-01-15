# RAG Document Q&A System

An AI-powered document question-answering system built from scratch using a custom RAG (Retrieval-Augmented Generation) pipeline.

## Tech Stack
- Python, FastAPI
- ChromaDB (vector store)
- OpenAI GPT API
- Sentence Transformers (embeddings)
- HTML, CSS, JavaScript (frontend)

## How It Works
1. Upload a PDF document
2. Text is extracted, chunked, and embedded into ChromaDB
3. Ask a question in natural language
4. Top-k relevant chunks are retrieved by cosine similarity
5. OpenAI GPT generates a context-aware answer

## Why RAG over ChatGPT directly?
- Handles large documents beyond token limits
- Keeps your data private
- Reduces hallucinations by grounding answers in document context
- Significantly cheaper at scale
