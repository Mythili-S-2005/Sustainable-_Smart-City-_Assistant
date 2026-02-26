# Sustainable Smart City Assistant 

The **Sustainable Smart City Assistant** empowers cities and citizens to thrive in an eco-conscious and connected urban environment.  
It leverages **IBM Watsonx Granite LLMs**, **Pinecone vector database**, and **real-time analytics** to optimize resources and deliver actionable sustainability insights.

---

## Features
- **Conversational Chat Assistant** – Natural language Q&A powered by IBM Watsonx Granite.  
- **Policy Summarization** – Converts lengthy government documents into concise, actionable summaries.  
- **Eco Tip Generator** – Personalized sustainability advice.  
- **Citizen Feedback Loop** – Collects and analyzes public feedback.  
- **KPI Forecasting** – Predicts trends in air quality, energy, and green cover.  
- **Anomaly Detection** – Flags unusual KPI/sensor values.  
- **Document & Data Search** – Semantic search with Pinecone embeddings.  
- **City Report Generator** – Automated sustainability reports.  
- **Multimodal Input** – Accepts PDFs, CSVs, text files.  
- **Interactive Dashboard** – User-friendly UI with Streamlit.  

---

##  Architecture

**Frontend (Streamlit):**
- Sidebar navigation for Chat, Policy Summarizer, Eco Tips, KPI Dashboard, Reports.  
- KPI visualizations with metrics, anomaly flags, charts.  

**Backend (FastAPI):**
- REST API endpoints for summarization, chat, eco-tips, feedback, reports, vector search.  
- Fully documented via Swagger UI (`/docs`).  

**LLM Integration (IBM Watsonx Granite):**
- IBM Cloud Granite family models via API key authentication.  
- Handles summarization, reporting, eco-tips, and chat.  

**Vector Search (Pinecone):**
- Stores embeddings for semantic policy & city data queries.  

**ML Modules:**
- Forecasting (scikit-learn regression).  
- Anomaly detection (threshold + statistical methods).  

---

##  Setup Instructions

### Prerequisites
- Python 3.9+  
- IBM Watsonx API key, Project ID, Model ID  
- Pinecone API key  
- Virtual environment + pip  

### Installation
```bash
git clone <your-repo-url>
cd smartcity-assistant-starter

# Create virtual environment
python -m venv .venv
# Windows
.\.venv\Scriptsctivate
# macOS/Linux
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Environment Variables (`.env`)
```env
WATSONX_API_KEY=your_ibm_key_here
WATSONX_PROJECT_ID=your_project_id_here
WATSONX_URL=https://eu-de.ml.cloud.ibm.com
WATSONX_MODEL_ID=ibm/granite-13b-instruct-v2

PINECONE_API_KEY=your_pinecone_key_here
PINECONE_ENV=us-east-1
INDEX_NAME=smartcity-policies
```

### Running
```bash
# Backend
uvicorn app.main:app --reload

# Frontend
streamlit run frontend/smart_dashboard.py
```

---

##  Folder Structure
```
app/
 ├── api/             # FastAPI routers
 ├── core/            # Config & Pinecone client
 ├── services/        # LLM, embeddings, forecasting, anomaly detection

frontend/
 └── smart_dashboard.py   # Streamlit frontend
```

---

##  API Endpoints
- `POST /chat/ask` → Smart city Q&A  
- `POST /policy/summarize` → Summarize policy text  
- `GET /eco/tips?topic=` → Eco tips  
- `POST /report/` → Generate sustainability report  
- `POST /vector/upsert` → Upload & embed documents  
- `GET /vector/search?query=` → Semantic search  
- `POST /feedback/` → Store citizen feedback  

---

##  Testing
- Unit tests for LLM prompts  
- API tests (Swagger, Postman)  
- Manual UI testing (frontend flows)  
- Edge cases → invalid inputs, large files, missing credentials  

---

##  Future Enhancements
- Role-based access (Admin, Citizen, Researcher)  
- Real-time IoT sensor integration   
- Multilingual support (IBM Watson Translator)  

---
