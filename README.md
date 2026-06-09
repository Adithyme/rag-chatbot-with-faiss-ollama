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

PDF Upload
↓
Text Extraction (PyPDFLoader)
↓
Text Chunking (LangChain Recursive Splitter)
↓
Embeddings (Sentence Transformers - MiniLM)
↓
Vector Store (FAISS)
↓
Semantic Search
↓
LLM (Ollama - Mistral)
↓
Final Answer Generation



### 🧰 Technologies Used (Local)
- LangChain
- FAISS
- HuggingFace Sentence Transformers
- Ollama (Mistral LLM)
- Streamlit
- PyPDF

---

## ☁️ Level 2 — FastAPI Deployment Layer (AWS EC2)

This layer exposes a lightweight API interface for the system.

Due to AWS Free Tier limitations, heavy ML models are NOT deployed on EC2.

Instead, FastAPI acts as an **API service layer**.

Client Request
↓
FastAPI (AWS EC2)
↓
Lightweight processing / API handling
↓
JSON response returned


### 🧰 Technologies Used (Cloud)
- FastAPI
- Uvicorn
- AWS EC2 (Ubuntu)
- Python Virtual Environment
- Git/GitHub for deployment

---

# ⚙️ Features

## 🧠 Local RAG System
- Upload and process PDF documents
- Intelligent text chunking
- Semantic search using FAISS
- Context-aware answers using Mistral LLM
- Streamlit-based interactive UI

## 🌐 FastAPI Cloud Layer
- REST API endpoints
- `/health` → system status check
- `/ask` → question answering endpoint
- AWS EC2 deployment with public access

---

# 📡 API Endpoints (FastAPI)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/health` | Check if server is running |
| POST | `/ask` | Send question to API |
| POST | `/upload_pdf` | Upload PDF (lightweight version) |

---

# 🏗️ Tech Stack

## 🧠 Machine Learning / RAG
- LangChain
- FAISS
- HuggingFace Transformers
- Sentence Transformers (MiniLM)
- Ollama (Mistral LLM)

## 🌐 Backend / Deployment
- FastAPI
- Uvicorn
- AWS EC2 (Ubuntu)
- Linux server management
- Git & GitHub

---

# 🚀 Deployment Architecture

            ┌──────────────────────┐
            │  Streamlit (Local)   │
            └─────────┬────────────┘
                      │
                      ▼
      ┌──────────────────────────────┐
      │   Local RAG System (Core)    │
      │  - FAISS                    │
      │  - Embeddings              │
      │  - Mistral LLM             │
      └──────────┬───────────────────┘
                 │
  ┌──────────────┴──────────────┐
  ▼                             ▼

  Local Execution AWS EC2 FastAPI
(Heavy ML Workload) (API Layer Only)


---

# 💡 Why This Architecture?

This hybrid design was implemented due to:

- ⚠️ AWS Free Tier limitations (CPU, RAM constraints)
- ⚠️ Heavy ML dependencies (FAISS, Transformers, LLMs)
- 🟢 Need to demonstrate real-world MLOps architecture

It reflects a **production-style separation of concerns** between ML and deployment layers.

---

# 🧪 Skills Demonstrated

## 🧠 Machine Learning / AI
- Retrieval-Augmented Generation (RAG)
- Vector similarity search
- Embedding-based retrieval
- LLM integration

## 🌐 Software Engineering / MLOps
- REST API development using FastAPI
- AWS EC2 deployment
- Linux server setup
- Git & GitHub version control
- System architecture design

---

# 📌 How to Run (Local RAG System)

```bash
pip install -r requirements.txt
streamlit run streamlit_upload_app.py

uvicorn backend.main:app --host 0.0.0.0 --port 8000

📈 Future Improvements
Full cloud-based RAG deployment (GPU EC2)
Docker containerization
CI/CD pipeline using GitHub Actions
Replace FAISS with managed vector DB (Pinecone / Weaviate)
Unified FastAPI + RAG integration on scalable infrastructure

🧠 Summary

This project demonstrates a real-world RAG system architecture combining:

Local ML execution for heavy AI workloads

"Cloud-based API deployment using FastAPI on AWS EC2"
