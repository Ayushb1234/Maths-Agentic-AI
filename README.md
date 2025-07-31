# Maths-Agentic-AI

Demo Video
---------

Features
✅ Math-only safe question handling (Guardrails: arithmetic regex + keyword detection)

✅ Vector DB-powered knowledge base (FAISS + HuggingFace embeddings)

✅ Web search fallback via MCP (future-proof)

✅ Direct arithmetic solver (e.g., 6+7)

✅ Human feedback capture (SQLite DB for future DSPy refinement)

✅ FastAPI backend, React frontend with real-time API calls

✅ Scalable architecture, easy to extend with new datasets (e.g., JEE Bench)

📂 Repository Structure
python
Copy
Edit
├── Math Agentic AI Backend.zip      # FastAPI backend services
├── math-agent-frontend.zip          # React frontend
├── README.md                        # Project documentation
└── data/                            # Dataset files (MathQA, etc.)
⚙️ Installation and Setup
1️⃣ Clone and Unzip
bash
Copy
Edit
git clone <your-repo-url>
cd <your-repo-name>
unzip "Math Agentic AI Backend.zip" -d backend
unzip "math-agent-frontend.zip" -d frontend
2️⃣ Backend Setup
Create a Python virtual environment:

bash
Copy
Edit
cd backend
python -m venv venv
source venv/Scripts/activate   # Windows
Install dependencies:

bash
Copy
Edit
pip install -r requirements.txt
Build/load the knowledge base:

bash
Copy
Edit
python scripts/ingest_mathqa.py
Start backend server:

bash
Copy
Edit
uvicorn main:app --reload --port 8000
3️⃣ MCP Server (Optional)
For web search fallback (runs on port 5001):

bash
Copy
Edit
uvicorn mcp_server.search_server:app --reload --port 5001
4️⃣ Frontend Setup
bash
Copy
Edit
cd ../frontend
npm install
npm start
Frontend runs at http://localhost:3000.

🧠 System Pipeline
mermaid
Copy
Edit
flowchart LR
User[User Question] --> G[Guardrails]
G -->|Arithmetic| A[Direct Solver]
G -->|Else| KB[Vector DB Search]
KB -->|Found| Ans[Return Answer]
KB -->|Not Found| MCP[MCP Web Search]
MCP --> Ans
Ans --> UI[React Frontend]
UI -->|Feedback| DB[SQLite feedback.db]
DB --> DSPy[Future DSPy Self-Learning]
📜 API Endpoints
POST /ask
json
Copy
Edit
{
  "question": "What is the derivative of x^2?"
}
✅ Returns:

json
Copy
Edit
{
  "question": "What is the derivative of x^2?",
  "answer": "The derivative of x^2 is 2x."
}
POST /feedback
Saves user rating:

json
Copy
Edit
{
  "question": "Explain Pythagoras theorem",
  "answer": "In a right triangle, a² + b² = c²",
  "rating": 1
}
📷 Screenshots
Feature	Screenshot
Frontend UI	
Backend Running	
Knowledge Base	

(Replace screenshots/... with actual paths in your repo.)

🎥 Demo Video
🎬 Watch Demo Video (Upload your screen recording to Google Drive or YouTube and paste the link here.)

💡 Future Enhancements
Add DSPy-based learning from user feedback

Deploy MCP server for real-time web search

Dockerize backend and frontend

Scale FAISS to Pinecone or Weaviate

🛠 Tech Stack
Backend: FastAPI, FAISS, HuggingFace Embeddings, SQLite

Frontend: ReactJS, Axios

AI Search: MCP Server (FastAPI microservice)

Dataset: MathQA + Custom Math Problems
