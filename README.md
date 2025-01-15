# RAG Document Q&A System

An AI-powered document question-answering system built from scratch using a custom RAG (Retrieval-Augmented Generation) pipeline - without any frameworks like LangChain.

## How It Works
1. Upload a PDF document via the web interface
2. Text is extracted, split into chunks, and converted to embeddings
3. Embeddings are stored in ChromaDB vector store
4. Ask a question in natural language
5. Top-k most relevant chunks are retrieved by cosine similarity
6. OpenAI GPT generates a context-aware answer grounded in the document

## Tech Stack
- **Backend**: Python, FastAPI, Uvicorn
- **Vector Store**: ChromaDB
- **Embeddings**: OpenAI Embeddings API
- **LLM**: OpenAI GPT API
- **PDF Processing**: PyMuPDF
- **Frontend**: HTML, CSS, JavaScript

## Why RAG over ChatGPT directly?
- Handles large documents beyond token limits
- Keeps your data private - document never leaves your server
- Reduces hallucinations by grounding answers in document context
- Significantly cheaper at scale - only relevant chunks sent to API
- Persistent knowledge base - upload once, query forever

## Setup

```bash
pip install fastapi uvicorn chromadb openai pymupdf python-dotenv

# Add your OpenAI API key to .env
echo "OPENAI_API_KEY=your_key_here" > .env

# Run the server
uvicorn main:app --reload
```

Visit `http://127.0.0.1:8000/docs` for the API documentation.

## Project Structure
```
rag-document-qa-scratch/
├── main.py          - FastAPI backend with RAG pipeline
├── static/
│   └── index.html   - Frontend UI
└── README.md
```

## Current Limitations & Future Improvements
This is a basic version built from scratch without frameworks. It can be significantly improved with:
- **LangChain Integration** - use LangChain's retrieval pipeline for cleaner code
- **Sentence Transformers** - replace OpenAI embeddings with local HuggingFace models (free, private)
- **Multi-document Support** - upload and query across multiple PDFs simultaneously
- **Chat History** - maintain conversation context across multiple questions
- **Source Citations** - show exactly which page/paragraph the answer came from
- **Document Management** - UI to upload, list, and delete documents
- **Authentication** - user accounts with private document storage
- **Cloud Deployment** - deploy on AWS/GCP with persistent vector storage
- **Support More Formats** - Word docs, PowerPoint, web URLs, not just PDFs