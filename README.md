# 🧠 AI Interview App

An AI-powered web application that enables interviewers to conduct automated, proctored technical interviews using coding, audio-based, and analytical assessments.

---

## 🔥 Features

- 🎤 **Audio Round with Transcription**
- 💻 **Coding IDE with Test Cases**
- 🎥 **Online Proctoring**
- 😊 **Sentiment Analysis**
- 📜 **Plagiarism Check**
- 📊 **Final Report Generation**

---

## 🛠️ Tech Stack

| Layer       | Tech                                |
|-------------|-------------------------------------|
| Frontend    | HTML, CSS, Bootstrap                |
| Backend     | Python (Flask)                      |
| Database    | MongoDB Atlas                       |
| AI Models   | OpenAI Whisper (transcription), VADER (sentiment), Python-diff for plagiarism |
| Dev Tools   | Git, GitHub, Postman                |

---

## 🚀 Run Locally

```bash
# Clone the repo
git clone https://github.com/your-username/ai-interview-app

# Set up virtual environment and install dependencies
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Add your MongoDB URI to a .env file
touch .env
echo "MONGO_URI=your_mongo_uri" >> .env

# Run backend
flask run
