 🧮 Maths Agentic AI – Agentic RAG-Based Math Tutor

[![Python](https://img.shields.io/badge/Python-3.11-blue)]()
[![FastAPI](https://img.shields.io/badge/FastAPI-Backend-green)]()
[![React](https://img.shields.io/badge/React-Frontend-blue)]()
[![FAISS](https://img.shields.io/badge/FAISS-VectorDB-orange)]()

An **AI-powered Math Professor-like agent** that provides **step-by-step solutions** to mathematical queries using a **Knowledge Base (MathQA dataset)**, **web search fallback (MCP)**, and **safe input/output guardrails**. It supports human feedback for future DSPy-based learning.

---

## 🎥 Demo Video

> 📌 [**Watch Demo Video**](https://drive.google.com/file/d/1L7DV06kCmatxfUukYC782zgeeqaxlhA-/view?usp=sharing) *(Upload your screen recording to Google Drive or YouTube and paste the link here)*

---

## ✅ Features

- 🔒 **Math-only safe question handling** (Guardrails: arithmetic regex + keyword detection)
- 📚 **Vector DB-powered knowledge base** (FAISS + HuggingFace embeddings)
- 🌐 **Web search fallback** via MCP (future-proof)
- ➕ **Direct arithmetic solver** (e.g., `6+7`)
- 📝 **Human feedback capture** (SQLite DB for future DSPy refinement)
- ⚡ **FastAPI backend**, **React frontend** with real-time API calls
- 🔄 **Scalable architecture**, easily extendable with new datasets (e.g., JEE Bench)

---

## 📂 Repository Structure

```plaintext
├── Math Agentic AI Backend.zip      # FastAPI backend services
├── math-agent-frontend.zip          # React frontend
├── README.md                        # Project documentation
└── data/                            # Dataset files (MathQA, etc.)
```
## Step 1
```plaintext
git clone <your-repo-url>
cd <your-repo-name>
unzip "Math Agentic AI Backend.zip" -d backend
unzip "math-agent-frontend.zip" -d frontend
```

## Step 2
```plaintext
cd backend
python -m venv venv
source venv/Scripts/activate   # Windows
pip install -r requirements.txt
python scripts/ingest_mathqa.py
uvicorn main:app --reload --port 8000
```

## Step 3
```plaintext
uvicorn mcp_server.search_server:app --reload --port 5001
```
## Step 4
```plaintext

cd ../frontend
npm install
npm start
```

Flowchart LR
------------

```plaintext
User[User Question] --> G[Guardrails]
G -->|Arithmetic| A[Direct Solver]
G -->|Else| KB[Vector DB Search]
KB -->|Found| Ans[Return Answer]
KB -->|Not Found| MCP[MCP Web Search]
MCP --> Ans
Ans --> UI[React Frontend]
UI -->|Feedback| DB[SQLite feedback.db]
DB --> DSPy[Future DSPy Self-Learning]
```
Screenshots
--------------
<img width="975" height="191" alt="image" src="https://github.com/user-attachments/assets/0be2b475-5d7f-4566-b258-b7aa9808e388" />
<img width="1257" height="331" alt="image" src="https://github.com/user-attachments/assets/d42027d4-cb93-4f3c-88b2-f611c8c40413" />
<img width="1198" height="281" alt="image" src="https://github.com/user-attachments/assets/efaf8bd0-32ce-4d07-97c7-67a31a810ad7" />
<img width="1394" height="847" alt="image" src="https://github.com/user-attachments/assets/d79f0ad2-9d9e-4f7b-b720-5880d25a67bb" />
<img width="1280" height="249" alt="image" src="https://github.com/user-attachments/assets/731fbc50-a85e-40c9-a9b8-f6e8ebcfc11f" />
---------------

💡 Future Enhancements
-----------------------
```plaintext
🔹 Add DSPy-based learning from user feedback

🔹 Deploy MCP server for real-time web search

🔹 Dockerize backend and frontend for easy deployment

🔹 Scale FAISS to cloud solutions like Pinecone or Weaviate

```

🛠 Tech Stack
--------------
```plaintext
Backend: FastAPI, FAISS, HuggingFace Embeddings, SQLite

Frontend: ReactJS, Axios

AI Search: MCP Server (FastAPI microservice)

Dataset: MathQA + Custom Math Problems
```
