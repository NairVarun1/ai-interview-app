# 📘 AI Interview App - Complete Documentation

---

## 📌 Overview

The **AI Interview App** is a web-based tool to help recruiters conduct interviews automatically and intelligently. The app allows candidates to take interviews online, using various modalities—coding questions, audio responses, and multiple assessments—while using AI for real-time evaluation.

---

## 🛠️ Tech Stack Summary

| Layer         | Tools/Tech Used                                     |
|---------------|-----------------------------------------------------|
| Frontend      | HTML5, CSS, Bootstrap                               |
| Backend       | Python (Flask)                                      |
| Database      | MongoDB Atlas                                       |
| AI Features   | OpenAI Whisper (or WhisperX), VADER, difflib        |
| DevOps        | Git, GitHub CLI                                     |

---

## 📁 Folder Structure

```
ai-interview-app/
├── backend/
│   ├── app.py
│   ├── routes/
│   │   ├── audio.py
│   │   ├── code.py
│   │   └── candidate.py
│   ├── models/
│   │   └── candidate.py
│   ├── services/
│   │   ├── transcription.py
│   │   ├── sentiment.py
│   │   └── plagiarism.py
│   ├── utils/
│   ├── .env
│   └── requirements.txt
├── frontend/
│   ├── pages/
│   │   ├── index.html
│   │   ├── instructions.html
│   │   ├── section.html
│   │   ├── ide.html
│   │   ├── audio.html
│   │   └── report.html
│   ├── static/
│   │   ├── css/
│   │   └── js/
├── docs/
│   ├── system_design.md
│   ├── ui_flow.md
│   ├── backend_endpoints.md
│   ├── model_workflow.md
│   └── setup_instructions.md
├── README.md
└── .gitignore
```

---

## 🎨 UI Flow (`docs/ui_flow.md`)

### 1. Candidate Info Page
- Collects name, email, address, etc.
- On submission: POST request to `/api/candidate`

### 2. Instructions Page
- Explains rules
- Tests mic and webcam access
- Proceeds only if access is granted

### 3. Section Selector
- Choose between: Coding Round, Audio Round, etc.

### 4. Coding Round
- Python-based editor
- Send code to backend `/api/code/run`
- Displays input/output and result

### 5. Audio Round
- Candidate records answer
- Sends audio blob to `/api/audio/submit`
- Backend transcribes and analyzes

### 6. Report Page
- Displays transcript
- Shows coding score, sentiment score
- Plagiarism percentage if applicable

---

## 🌐 Backend API (`docs/backend_endpoints.md`)

### POST `/api/candidate`
- Saves candidate info to MongoDB

### POST `/api/code/run`
- Takes code input
- Runs securely in Python subprocess
- Returns result with output/status

### POST `/api/audio/submit`
- Accepts audio blob
- Runs Whisper transcription
- Runs sentiment on transcript
- Returns transcript + sentiment

### GET `/api/report/:id`
- Fetches final report by candidate ID

---

## 🤖 Model Workflow (`docs/model_workflow.md`)

### 🎤 Audio Transcription
- Accept audio in `.webm` or `.wav`
- Run through Whisper API / local model
- Return transcript (text)

### 😊 Sentiment Analysis
- Use `nltk.sentiment.vader.SentimentIntensityAnalyzer`
- Input: transcript
- Output: Positive / Negative / Neutral score

### 📜 Plagiarism Check
- Compare submitted answers using `difflib.SequenceMatcher`
- Flag high similarity

---

## 🧩 System Design (`docs/system_design.md`)

### Architecture Diagram
```
[Browser]
   |
   v
[Flask Backend API] <---> [MongoDB Atlas]
     |      |      |
     |      |      └── Plagiarism Check
     |      └── Sentiment Analyzer
     └── Whisper Transcriber
```

### Workflow
1. Candidate visits frontend → fills form → starts interview
2. UI talks to backend via fetch/axios
3. All data is saved in MongoDB
4. AI modules run in background
5. Final report is generated and served

---

## 🧪 Setup Instructions (`docs/setup_instructions.md`)

### Install Backend
```bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
touch .env
```
Add MongoDB URI to `.env`:
```
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/myInterviewDB
```

### Install Frontend
- Just open `frontend/pages/index.html` in your browser

### Run Flask Server
```bash
flask run
```

---

## ✅ To-Do Checklist

- [x] Setup MongoDB Atlas
- [x] Setup GitHub Repo
- [x] Design Frontend UI Pages
- [x] Backend Flask API Setup
- [x] Connect MongoDB
- [ ] Integrate Whisper for transcription
- [ ] Add VADER sentiment analysis
- [ ] Add plagiarism logic
- [ ] Generate reports

