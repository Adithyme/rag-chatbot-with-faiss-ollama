# rag-chatbot-with-faiss-ollama
PDF-based RAG chatbot using LangChain, FAISS, Hugging Face embeddings, Ollama, and Mistral for semantic document question answering.
# PDF RAG Chatbot using LangChain, FAISS and Ollama

## Overview

Built a Retrieval-Augmented Generation (RAG) chatbot that allows users to upload PDF documents and ask questions about their content.

The system processes PDFs, generates embeddings using Sentence Transformers, stores vectors in FAISS, retrieves relevant chunks, and generates answers using the Mistral LLM running locally through Ollama.

## Features

- Upload any PDF document
- Automatic text chunking
- Semantic search using FAISS
- Local embeddings using MiniLM
- Local LLM inference using Mistral
- Streamlit user interface
- Retrieval accuracy evaluation framework

## Tech Stack

- Python
- LangChain
- FAISS
- Hugging Face Embeddings
- Ollama
- Mistral
- Streamlit

## Workflow

PDF Upload
↓
PyPDFLoader
↓
Text Chunking
↓
Embeddings Generation
↓
FAISS Vector Store
↓
Semantic Retrieval
↓
Mistral LLM
↓
Answer Generation

## Evaluation

- Retrieval Accuracy: 95%
- Evaluated on custom LLM interview dataset

## Run Locally

pip install -r requirements.txt

streamlit run streamlit_upload_app.py

## Application Preview

![Upload](screenshots/upload_page.png)

![Chat](screenshots/answer_page.png)
