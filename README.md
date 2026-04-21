# 🏦 CredNova — AI Credit Risk Scoring Platform

> **Your credit story, full clarity, anytime.**

🚀 A full-stack fintech platform that simulates real-world credit underwriting using **Machine Learning, Explainable AI (SHAP), and alternative financial data (bank statements)**.



<p align="center">
  <a href="https://crednova.vercel.app"><b>🌐 Live Demo</b></a> •
  <a href="#features"><b>✨ Features</b></a> •
  <a href="#architecture"><b>🏗️ Architecture</b></a> •
  <a href="#setup"><b>⚙️ Setup</b></a>
</p>

---

## ⚡ Key Highlights

* 🧠 **Calibrated ML Model** (LightGBM + Probability Mapping)
* 🔍 **Explainable AI (SHAP)** for transparent decisions
* 📄 **Bank Statement Parsing** → Feature Engineering Pipeline
* 💳 **Thin-file Applicant Support** (No CIBIL required)
* 🤖 **LLM-generated Underwriting Insights**
* ⚡ **Full-stack System** (React + FastAPI + MongoDB)

---

## 📌 What is CredNova?

CredNova is an **AI-powered credit evaluation system** that helps lenders decide whether to approve or reject a loan — even for users with little or no credit history.

Instead of relying only on traditional credit scores, it analyzes:
- 📄 Bank statements (spending patterns, cash flow)
- 📊 Financial behavior (UPI usage, cash ratio, transactions)
- 🧠 Machine learning risk predictions (Probability of Default)
- 🔍 Explainable AI (SHAP) to justify every decision

---

### 🎯 In simple terms

CredNova acts like a **digital loan officer powered by AI**:

- 👤 **Applicant** → submits financial data (even without CIBIL score)  
- ⚙️ **System** → processes data + runs ML model  
- 🧠 **AI** → calculates credit score + risk level  
- 🏦 **Bank/Admin** → gets clear insights to approve/reject  

---

### 💡 Why it matters

Traditional systems fail for **thin-file users** (no credit history).  
CredNova solves this by using **alternative data + explainable AI**, making credit access more inclusive and transparent.
---

## 📸 Product Screens

### 🌐 Landing Experience (Hero)

<p align="center">
  <img src="https://github.com/user-attachments/assets/3edc20b8-727e-4228-ab12-1bcb655886e0" width="90%" />
</p>

---

### 🧠 AI Insights Dashboard

<p align="center">
  <img src="https://github.com/user-attachments/assets/afb6c2ce-7f77-428f-b7f8-08d68eff7762" width="90%" />
</p>

✔ Credit score + risk band
✔ ML-based insights
✔ Feature-level explainability
✔ Spending behavior signals

---

### 🔄 AI Pipeline Flow

<p align="center">
  <img src="https://github.com/user-attachments/assets/bf216375-dcc0-4848-ab91-2eb613c29c34" width="90%" />
</p>

From identity → bank data → ML scoring → SHAP → decision support

---

### 🏦 Bank Employee Dashboard

<p align="center">
  <img src="https://github.com/user-attachments/assets/63e7bd7e-0931-4ab8-a5ff-0cf767b0232c" width="90%" />
</p>

✔ Loan decision support
✔ Risk indicators
✔ SHAP explanations
✔ Approve / Reject workflows

---

## Features

### 👤 Applicant Side

* Loan application & onboarding
* Thin-file support (no credit history)
* Psychometric score integration
* Bank statement PDF upload
* Real-time dashboard with insights

---

### 🏛️ Admin / Bank Employee

* Application review workflows
* AI-generated underwriting summaries
* Risk signals & explainability
* Multi-application aggregation
* Decision support system

---

### 🤖 ML & AI Core

* LightGBM + scikit-learn pipeline
* Probability of Default (PD) → Credit Score mapping
* Risk band classification
* SHAP feature attribution
* Retrieval-based explanation system
* LLM narratives (Ollama / OpenAI optional)

---

### 📄 Bank Statement Processing

* PDF parsing using pdfplumber
* Transaction cleaning & categorization
* UPI velocity & cash ratio features
* Direct integration into ML pipeline

---

## Architecture

<p align="center">
  <img src="https://github.com/user-attachments/assets/f75b9989-de01-4ae5-aa1c-46fcfd6bdd06" width="90%" />
</p>

### 🔁 Data Flow

User → Frontend → Backend → Feature Engineering → ML Model → SHAP → LLM Insights → Dashboard

## ⚡ Why This Architecture Works

- Scalable: ML runs as independent service  
- Interpretable: SHAP ensures transparent decisions  
- Flexible: Supports thin-file users and alternative data  
- Production-ready: Mirrors real-world fintech systems  
---
## 📊 ML Pipeline

```
Raw Data
   ↓
Preprocessing (sklearn)
   ↓
LightGBM Model
   ↓
Probability of Default (PD)
   ↓
├── Credit Score (300–900)
├── Risk Band
├── Loan Eligibility
└── SHAP Explainability
        ↓
   LLM Narratives
```

---

## 🛠️ Tech Stack

### Frontend

* React 19 + TypeScript + Vite
* Tailwind CSS
* React Router
* TanStack Query
* Recharts
* Clerk Authentication

### Backend

* FastAPI + Uvicorn
* Pydantic v2
* MongoDB (PyMongo)
* httpx (async APIs)

### ML / AI

* LightGBM
* scikit-learn
* SHAP
* pandas, NumPy
* Ollama (Mistral)
* OpenAI (optional)

### PDF Processing

* pdfplumber

---

## ⚙️ Environment Variables

### Backend

```
MONGO_URI=your_mongodb_uri
CREDIT_MODEL_URL=your_model_url
OPENAI_API_KEY=optional
CLERK_SECRET_KEY=your_key
```

### Frontend

```
VITE_API_BASE_URL=your_backend_url
VITE_CLERK_PUBLISHABLE_KEY=your_key
```

---

## Setup

### 1. Clone Repositories

```
https://github.com/Aditya9207/CredNova-Frontend.git
https://github.com/Aditya9207/CredNova-Backend.git
```

---

### 2. Frontend

```
cd CredNova-Frontend
npm install
npm run dev
```

---

### 3. Backend

```
cd CredNova-Backend
pip install -r requirements.txt
uvicorn main:app --reload
```

---

### 4. ML Service

```
cd crednova-ml
pip install -r requirements.txt
uvicorn model_server:app --reload
```

---

## 📁 Project Structure

```
crednova-backend/
├── routes/
├── services/
├── models/
├── db/
├── ml/
└── main.py
```

---

## 🎯 Use Cases

* Credit risk evaluation
* Loan underwriting simulation
* Alternative credit scoring (thin-file users)
* Explainable AI in finance
* Fintech product prototyping

---

## 👤 Author

**Aditya Jamdade**

📧 [jamdadeaditya05@gmail.com](mailto:jamdadeaditya05@gmail.com)

💼 [LinkedIn](www.linkedin.com/in/adityajamdade)  

🐙 [GitHub](https://github.com/Aditya9207)

---

## 🏷️ Keywords

Full-stack · React · FastAPI · Machine Learning · Credit Risk · SHAP · Explainable AI · LightGBM · Fintech · MongoDB · PDF Parsing · Feature Engineering

---

## 📄 License

MIT License — free to use and modify.
