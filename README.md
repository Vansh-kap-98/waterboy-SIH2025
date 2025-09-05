# 💧 WATERBOY – AI Groundwater Chatbot

WATERBOY is an **AI-powered chatbot** that helps explore and analyze groundwater data.  
It combines a **React + Vite frontend** with a **Python backend** powered by **LangChain** and **TinyLlama**, providing insights from groundwater reports using **retrieval-augmented generation (RAG)**.  

---

## ✨ Features
- 🔍 **Question answering** from groundwater dataset (CSV reports).  
- 📊 **FAISS vector search** + **HuggingFace embeddings** for efficient retrieval.  
- 🧠 **TinyLlama local model** with LangChain QA pipeline.  
- 🎨 **Modern chat UI** with light/dark themes and suggested prompts.  
- 🌐 **API-first design** (Flask backend, React frontend).  
- 📱 **Responsive design** for desktop & mobile.  

---

## 🛠️ Tech Stack

### **Frontend**
- React + Vite  
- TailwindCSS (for styling)  
- Fetch API for backend connection  

### **Backend**
- Flask + Flask-CORS  
- LangChain  
- FAISS (vector store)  
- HuggingFace embeddings (`BAAI/bge-large-en-v1.5`)  
- LlamaCpp + TinyLlama (`tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf`)  

---

## 📂 Project Structure
waterboy-chatbot/
│
├── backend/ # Python backend (Flask + LangChain)
│ ├── app.py # Main API server
│ ├── CentralReport.csv # Groundwater dataset
│ ├── requirements.txt # Python dependencies
│
├── frontend/ # React + Vite frontend
│ ├── index.html
│ ├── src/
│ │ ├── App.jsx # Main UI
│ │ ├── Chatbot.jsx # Chat component
│ │ ├── api.js # API calls
│ ├── package.json
│ ├── vite.config.js
│ ├── .env # Backend API URL config
│
└── README.md

yaml
Copy code

---

## ⚙️ Setup Guide

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/waterboy-chatbot.git
cd waterboy-chatbot
2. Backend Setup (Flask + LangChain + TinyLlama)
bash
Copy code
cd backend
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

pip install -r requirements.txt
Required files:

CentralReport.csv → dataset for groundwater reserves.

tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf → TinyLlama model (download separately).

Run the backend:

bash
Copy code
python app.py
Backend will start at:
👉 http://localhost:5000/api/ask

Test it:

bash
Copy code
curl -X POST http://localhost:5000/api/ask \
  -H "Content-Type: application/json" \
  -d '{"question": "What is the groundwater recharge in Jaipur district?"}'
3. Frontend Setup (React + Vite)
bash
Copy code
cd frontend
npm install
npm run dev
Frontend will start at:
👉 http://localhost:5173

4. Configure API URL
Create .env in frontend/:

bash
Copy code
VITE_API_URL=http://localhost:5000/api/ask
Update fetch calls:

javascript
Copy code
const response = await fetch(import.meta.env.VITE_API_URL, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ question: userMessage.text }),
});
🖼️ Usage
Open the frontend in your browser.

Choose a suggested prompt (e.g., “GROUNDWATER LEVEL FOR JAIPUR”) or type your own.

WATERBOY fetches data from the backend and responds with precise answers.

Toggle 🌙 Dark/☀️ Light theme anytime.

🚀 Future Improvements
🔄 Token streaming for real-time responses.

📑 Support for multiple datasets (multi-region groundwater reports).

🧮 Advanced analytics (forecasting, anomaly detection).

☁️ Deploy backend (AWS/GCP) + frontend (Vercel/Netlify).
