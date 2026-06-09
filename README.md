 PDF RAG Chatbot with Split Architecture (Local RAG + AWS API)

A Retrieval-Augmented Generation (RAG) system for querying PDF documents, built using LangChain, FAISS, Hugging Face embeddings, and Mistral LLM, with a split architecture deployment approach:

 Core RAG system runs locally
 FastAPI service deployed on AWS EC2 for API exposure
 Project Overview

This project demonstrates a full end-to-end RAG pipeline for document question answering.

It is designed with a real-world deployment architecture, separating:

Heavy ML computation (local environment)
Lightweight API serving (cloud deployment)
 System Architecture
 Level 1 — Local RAG System (Core AI Engine)

This part runs locally due to heavy dependencies.

PDF Upload
   ↓
Text Extraction (PyPDFLoader)
   ↓
Text Chunking (LangChain)
   ↓
Embeddings (HuggingFace MiniLM)
   ↓
Vector Store (FAISS)
   ↓
Semantic Search
   ↓
LLM (Ollama - Mistral)
   ↓
Final Answer Generation
✔ Technologies Used (Local)
LangChain
FAISS
HuggingFace Embeddings (MiniLM)
Ollama (Mistral LLM)
Streamlit (UI)
PyPDF
☁️ Level 2 — AWS FastAPI Deployment Layer

This part is deployed on AWS EC2 (Free Tier).

It acts as a lightweight API layer to expose functionality.

Client Request
   ↓
FastAPI (AWS EC2)
   ↓
Lightweight processing / endpoint handling
   ↓
Returns response (JSON)
✔ Technologies Used (Cloud)
FastAPI
Uvicorn
AWS EC2 (Ubuntu)
Python Virtual Environment
🔗 Key Design Decision (Important)

Due to AWS Free Tier limitations:

 Heavy ML models (FAISS, Transformers, Mistral) are NOT run on EC2
 Core RAG system runs locally
 AWS is used only for API deployment and MLOps demonstration
 Features
 Local RAG System
Upload and process PDF documents
Chunk-based text processing
Semantic search using FAISS
Context-aware responses using Mistral LLM
Streamlit UI for interaction
Cloud API Layer
FastAPI REST endpoints
/health for service monitoring
/ask for query handling
AWS EC2 deployment with public IP access
 API Endpoints (FastAPI)
Method	Endpoint	Description
GET	/health	Check server status
POST	/ask	Submit question
POST	/upload_pdf	Upload document (demo/light version)
Tech Stack
ML / RAG Layer
LangChain
FAISS
HuggingFace Transformers
Mistral (Ollama)
PyPDF
Deployment Layer
FastAPI
Uvicorn
AWS EC2 (Ubuntu)
Linux environment management
Deployment Architecture
          ┌────────────────────────────┐
          │   Streamlit (Local UI)     │
          └────────────┬───────────────┘
                       │
                       ▼
          ┌────────────────────────────┐
          │  Local RAG Engine          │
          │  (FAISS + LLM + Embeds)    │
          └────────────┬───────────────┘
                       │
        ┌──────────────┴──────────────┐
        │                             │
        ▼                             ▼
 Local Execution              AWS EC2 Deployment
 (Heavy ML Tasks)            (FastAPI API Layer)
 Why This Architecture?

This split design was chosen due to:

 AWS Free Tier limitations (CPU, RAM)
 Heavy ML dependencies (FAISS, Transformers, Mistral)
 Need for scalable API deployment practice

This simulates a real-world MLOps separation of concerns.

 Skills Demonstrated
Retrieval-Augmented Generation (RAG)
Vector databases (FAISS)
Embedding models
LLM integration (Ollama + Mistral)
REST API development (FastAPI)
AWS EC2 deployment
Linux server management
System architecture design
 How to Run (Local RAG)
pip install -r requirements.txt
streamlit run streamlit_upload_app.py
How to Run (AWS FastAPI)
uvicorn backend.main:app --host 0.0.0.0 --port 8000
 Future Improvements
Full cloud deployment with GPU EC2
Docker containerization
CI/CD pipeline (GitHub Actions)
Vector DB migration to Pinecone/Weaviate
Unified cloud-based RAG system
Summary

This project demonstrates:

A production-inspired RAG system with a hybrid architecture combining local ML execution and cloud-based API deployment.


