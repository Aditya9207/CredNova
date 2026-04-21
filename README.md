🏦 CredNova — Credit Risk Scoring & Loan Application Platform
Full-stack credit risk scoring and loan application platform combining calibrated ML, SHAP-based explainability, alternative/thin-file applicant signals, bank statement PDF ingestion, and admin review workflows — with JWT-style auth via Clerk and persistence in MongoDB.

🔗 Quick Links
Resource	Link
🖥️ Frontend Repository	CredNova-fe
⚙️ Backend Repository	CredNova-be
🤖 ML Model Repository	(add link)
🌐 Live Frontend URL	https://crednova.vercel.app (replace)
🚀 Backend API URL	https://crednova-api.onrender.com (replace)
📊 ML Model Hosted URL	https://crednova-model.onrender.com (replace)
🎥 Demo Video	(add link)
📌 What is CredNova?
CredNova is a fintech platform that simulates a real-world credit underwriting system. It enables applicants to apply for loans, processes their data through a calibrated ML pipeline, and provides explainable AI-driven risk assessments to admins and bank employees — all through a modern, responsive web interface.

Core System Capabilities
Credit Scoring Pipeline — Loads a production-style joblib bundle (preprocessor + probability calibration + SHAP explainer). Maps default probability (PD) to an alternative bureau-style score, risk tiers, and sanction/eligible amount logic; supports aggregating multiple applications per user (weighted scoring in inference_utils).

Explainable AI (XAI) — SHAP top-k features paired with a JSON knowledge base (feature_explanations.json) for retrieval-augmented style explanations; LLM-generated professional remarks via Ollama for richer admin narratives.

Thin-file / Gig-economy Support — Form + API support for applicants without traditional CIBIL (no_cibil_score), plus psychometric score capture and validation.

Bank Statement Path — PDF upload → parse/clean/categorize transactions → derive UPI/cash-ratio style features for the deployed ML microservice; spending insights via rule-based categorization + optional LLM JSON output (insights_service).

Product Surfaces — Applicant onboarding, credit AI apply + dashboard (charts, loading UX, code-split lazy routes), bank employee view, admin flows: application summaries, status updates, AI insight generation, user notifications.

✨ Features
👤 Applicant Side
Onboarding and loan application form
Support for thin-file / gig-economy applicants (no CIBIL score path)
Psychometric score capture and validation
Bank statement PDF upload for alternative data signals
Real-time application status and dashboard with charts
🏛️ Admin / Bank Employee Side
Application summary and review workflows
AI-generated underwriting narratives (Ollama / optional OpenAI)
Application status updates and user notifications
Aggregated scoring across multiple applications per user
🤖 ML & AI Core
Calibrated LightGBM + scikit-learn pipeline (joblib serialized)
Probability of Default (PD) → bureau-style score → risk tier mapping
SHAP-based feature attribution for transparent decisions
Retrieval-augmented explanation KB (feature_explanations.json)
LLM-generated professional remarks via Ollama (Mistral)
Optional OpenAI (gpt-4o-mini) for spending narratives
📄 Bank Statement Processing
pdfplumber based PDF → table/text extraction
pandas-centric cleaning and rule-based spend categorization
UPI / cash-ratio style feature derivation
Feeds directly into the deployed ML microservice
🛠️ Tech Stack
Frontend
Layer	Tech
Framework	React 19, TypeScript, Vite 7
Styling	Tailwind CSS
Routing	React Router 7
State / Data	TanStack React Query
Charts	Recharts
UI	Ant Design Icons, Lucide, Sonner (toasts)
Auth	Clerk (@clerk/clerk-react, protected routes)
Backend
Layer	Tech
Framework	FastAPI, Uvicorn
Validation	Pydantic v2
HTTP Client	httpx (async, external credit model on Render)
CORS	FastAPI CORS Middleware
Config	Environment-based URLs (CREDIT_MODEL_URL, MONGO_URI, API keys)
Database
Layer	Tech
Primary DB	MongoDB (PyMongo)
DB Name	crednova
Collections	users, credit_applications
Async Pattern	Motor (listed for async flows)
ML / AI
Layer	Tech
Models	LightGBM, scikit-learn
Serialization	joblib (preprocessor + calibrated classifier pipeline)
Explainability	SHAP explainers
Data Processing	pandas, NumPy, SciPy
LLM (local)	Ollama + Mistral
LLM (cloud)	OpenAI gpt-4o-mini (optional, spending narratives)
PDF Parsing	pdfplumber (PDF → tables/text → features)
🏗️ Architecture Overview
┌─────────────────────────────────────────────┐
│              React 19 Frontend               │
│     (Vite, TypeScript, Tailwind, Clerk)      │
└──────────────────┬──────────────────────────┘
                   │ REST API (JSON)
┌──────────────────▼──────────────────────────┐
│            FastAPI Backend                   │
│     (Pydantic v2, JWT via Clerk, CORS)       │
│                                              │
│  ┌─────────────┐    ┌──────────────────┐    │
│  │   MongoDB   │    │  PDF Ingestion   │    │
│  │  (PyMongo)  │    │  (pdfplumber +   │    │
│  └─────────────┘    │   pandas)        │    │
│                     └──────────────────┘    │
└──────────────────┬──────────────────────────┘
                   │ httpx async calls
┌──────────────────▼──────────────────────────┐
│         ML Microservice (Render)             │
│                                              │
│  LightGBM + scikit-learn + SHAP             │
│  PD → Score → Risk Tier → Eligibility       │
│  SHAP attribution + KB explanations         │
│  Ollama / OpenAI narrative generation       │
└─────────────────────────────────────────────┘
⚙️ Environment Variables
Backend .env
MONGO_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/crednova
CREDIT_MODEL_URL=https://crednova-model.onrender.com
OPENAI_API_KEY=your_openai_key_here       # optional
CLERK_SECRET_KEY=your_clerk_secret_key
Frontend .env
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
VITE_API_BASE_URL=https://crednova-api.onrender.com
🚀 Getting Started
1. Clone all repos
git clone https://github.com/Adarsh-griffin/CredNova-fe.git
git clone https://github.com/Adarsh-griffin/CredNova-be.git
git clone *(add ml model repo)*
2. Frontend Setup
cd crednova-frontend
npm install
cp .env.example .env   # fill in your keys
npm run dev
3. Backend Setup
cd crednova-backend
pip install -r requirements.txt
cp .env.example .env   # fill in your keys
uvicorn main:app --reload
4. ML Model Setup
cd crednova-ml-model
pip install -r requirements.txt
uvicorn model_server:app --reload --port 8001
📊 ML Pipeline Details
Raw Applicant Data
       │
       ▼
Preprocessor (sklearn Pipeline)
       │
       ▼
Calibrated LightGBM Classifier
       │
       ▼
Probability of Default (PD)
       │
       ├──► Bureau-style Credit Score (300–900)
       ├──► Risk Tier (Low / Medium / High / Very High)
       ├──► Sanction Amount Eligibility
       └──► SHAP Top-K Feature Attribution
                    │
                    ▼
         feature_explanations.json (KB)
                    │
                    ▼
         Ollama / OpenAI Narrative
📁 Project Structure
crednova-backend/
├── main.py                    # FastAPI entry point
├── routes/
│   ├── auth.py
│   ├── applications.py
│   └── admin.py
├── services/
│   ├── inference_utils.py     # ML scoring logic
│   ├── insights_service.py    # LLM narrative generation
│   └── pdf_parser.py          # Bank statement ingestion
├── models/
│   └── schemas.py             # Pydantic v2 models
├── db/
│   └── mongo.py               # PyMongo connection
└── ml/
    ├── pipeline.joblib        # Serialized ML pipeline
    ├── shap_explainer.joblib
    └── feature_explanations.json
👤 Author
Aditya Jamdade

📧 jamdadeaditya05@gmail.com
💼  
🐙
🏷️ ATS / LinkedIn Keywords
Full-stack development · React · TypeScript · Vite · Tailwind CSS · FastAPI · REST APIs · Pydantic · MongoDB · Machine learning · Credit risk · Model calibration · SHAP · Explainable AI (XAI) · scikit-learn · LightGBM · pandas · PDF parsing · Feature engineering · Microservices integration · Clerk · React Query · CI-friendly build

📄 License
MIT License — feel free to use this as a reference or portfolio project.
