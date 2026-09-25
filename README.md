# AI Resume Analyzer 📄✨

> **Upload your resume, get instant AI-powered feedback on ATS compatibility, keyword gaps, and improvement suggestions.**

A high-performance, full-stack **MERN** web application (MongoDB, Express, React + Vite, Node.js) that extracts text from resumes in multiple formats (**PDF, DOCX, TXT**), evaluates them against Applicant Tracking System (ATS) industry standards, and provides actionable recommendations using the proven **Google X-Y-Z / STAR formula**.

---

## 🌟 Key Features

1. **Multi-Format Native Text Extraction**:
   - Parses native text from `.pdf`, `.docx`, `.doc`, and `.txt` files in memory with zero disk clutter.
2. **ATS Scoring & Radial Dial Gauge**:
   - Overall composite score (0–100) with grade badges (`A+`, `A`, `B`, `C`, `D`).
   - Detailed sub-scores for:
     - ATS Compatibility & Section Parsing
     - Role Keyword & Skills Alignment
     - Content Impact & Strong Action Verbs
     - Bullet Formatting & Line Length
     - Brevity & Word Count Health
3. **Keyword Gap & Competency Analysis**:
   - Matched role skills (with occurrence counts, e.g. `React (4x)`, `Node.js (3x)`).
   - Missing critical keywords categorized by importance (`Critical`, `High`, `Medium`).
   - Overused buzzwords & filler phrases flags (e.g. `team player`, `hard worker`).
   - Detection of quantifiable metrics (`%`, `$`, scale numbers).
4. **Google X-Y-Z / STAR Bullet Enhancer**:
   - Automatically detects passive duty statements (e.g. *"Responsible for fixing bugs and updating website features"*).
   - Generates high-impact, quantifiable rewrites (*"Accomplished [X], as measured by [Y], by doing [Z]"*).
   - 1-click clipboard copy with visual feedback.
5. **Interactive Live Bullet Rewriter Sandbox**:
   - Paste any resume bullet point, select your target role, and instantly generate 3 distinct variation styles:
     - **Metric-Driven** (Numbers, %, scale)
     - **Leadership & Architecture** (Initiative, system design)
     - **Concise ATS Power** (High keyword density, punchy)
6. **Section Health Diagnostic**:
   - Health check for Contact Info (Email, Phone, LinkedIn, GitHub), Professional Summary, Work Experience, Education, Skills, and Certifications.
   - Raw ATS parser text view showing exactly how automated scanners view your resume.
7. **Instant 1-Click Sample Resumes**:
   - Test immediately without uploading a file:
     - *Alex Rivera* (Senior Full Stack Engineer — 98% Elite match)
     - *Jordan Parker* (Mid-Level Developer — Needs work, passive verbs)
     - *Dr. Priya Sharma* (Data Scientist & ML Engineer)
8. **Analysis History & Persistence (MongoDB)**:
   - Stores all analyses in MongoDB with Mongoose.
   - Includes graceful in-memory fallback if MongoDB is offline.
   - History drawer with instant reload, score comparisons, and report deletion.
9. **Export & Print**:
   - 1-click formatted ATS Audit Report print / Save-as-PDF.
   - Export analysis details as structured JSON.
10. **Dual AI Engine**:
    - **Engine 1**: Built-in deterministic NLP & heuristic ATS parser (runs 100% offline, zero API key required).
    - **Engine 2**: Google Gemini Generative AI layer for deep qualitative recruiter impression and bespoke advice when an API key is provided.

---

## 🛠️ Architecture & Tech Stack

- **Frontend**:
  - React 19 + Vite 8
  - Modern Vanilla CSS with responsive design system, CSS variables, and glassmorphic cards
  - Lucide React (feather-style icons)
  - Canvas Confetti (celebratory milestone animations)
- **Backend**:
  - Node.js (ESM) + Express.js
  - Multer (Memory Storage)
  - `pdf-parse` (Native PDF parser)
  - `mammoth` (DOCX parser)
  - `@google/generative-ai` (Gemini API integration)
- **Database**:
  - MongoDB + Mongoose (`ResumeAnalysis` schema)
  - Resilient hybrid mode with in-memory caching fallback

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- Node.js 18+ installed
- MongoDB (optional, auto-detected)

### 2. Running the Full Stack App
From the root directory (`ai-resume-analyzer`):

```bash
# Start both Backend (Port 5000) and Frontend (Port 3000) concurrently:
npm run dev
```

Or run separately:
```bash
# Backend
cd server
npm run dev

# Frontend
cd client
npm run dev
```

- **Frontend Application**: `http://localhost:3000`
- **Backend API & Health**: `http://localhost:5000/api/health`

---

## 📡 API Reference

| Endpoint | Method | Description |
|---|---|---|
| `/api/health` | `GET` | Health check & MongoDB status |
| `/api/roles` | `GET` | Pre-configured role benchmarks & keyword sets |
| `/api/samples` | `GET` | Instant demo candidate profiles |
| `/api/analyze` | `POST` | Upload file (`multipart/form-data`) + role + JD |
| `/api/analyze-sample` | `POST` | 1-click test of pre-configured sample |
| `/api/rewrite-bullet` | `POST` | Interactive live bullet point rewriter |
| `/api/history` | `GET` | Retrieve past saved analyses from MongoDB |
| `/api/history/:id` | `GET` | Retrieve single analysis details |
| `/api/history/:id` | `DELETE` | Delete saved report |
