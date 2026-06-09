# 📚 PDF RAG Chatbot with FastAPI, FAISS & LLM (Split Architecture)

A Retrieval-Augmented Generation (RAG) system for querying PDF documents using **LangChain, FAISS, HuggingFace embeddings, and Mistral LLM**, with a **split architecture design**:

- 🧠 Core RAG system runs locally (heavy ML workload)
- 🌐 FastAPI backend deployed on AWS EC2 (lightweight API layer)

---

# 🚀 Project Overview

This project is a **PDF-based Question Answering system** that allows users to upload documents and ask natural language questions.

It implements a full **RAG (Retrieval-Augmented Generation) pipeline**, combining:

- Document understanding
- Semantic search
- LLM-based response generation

Due to infrastructure constraints (AWS Free Tier), the system is designed using a **hybrid architecture**.

---

# 🧠 System Architecture

## 🟢 Level 1 — Local RAG System (Core AI Engine)

This part runs locally due to heavy ML dependencies.


