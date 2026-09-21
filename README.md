# 🌐 LangID — Neural Language Intelligence

LangID is a real-time, AI-powered multilingual speech and text intelligence system. It captures live audio or text input, identifies the spoken/written language, transcribes and translates it, detects emotion, and includes two built-in AI assistants — a general-purpose chatbot and a college helpdesk assistant for **AUCE (Andhra University College of Engineering)**.

Built with a **Flask + Google Gemini API** backend and a single-page, no-framework **HTML/CSS/JavaScript** frontend.

🌐 **Live Project:** [LangID](https://naramalapavanakumar.github.io/LANGID/)

## ✨ Features

- 🎙️ **Real-time audio language detection** — record from the mic and get language, confidence score, language family, script, and region
- 📝 **Live transcription** with English and Hindi translations
- 😊 **Emotion analysis** — detects speaker emotion (happy, neutral, sad, angry, surprised, fearful) with confidence
- 🔀 **Code-switching detection** — flags multiple languages used in one clip, with secondary languages listed
- 🌍 **Text-based language detection** — paste text to identify language, script, and get translations
- 🔁 **Translate to any language** on demand
- 🤖 **ZARA** — an AI helpdesk assistant pre-loaded with an AUCE knowledge base (HODs, bus routes, hostel info, canteen prices, placements, contacts) that replies in the user's chosen language
- 💬 **Ask Anything** — a general-purpose conversational AI assistant with voice input and multilingual replies
- 🗣️ Browser-based voice recognition using the Web Speech API for wake-word/voice-triggered interactions
- 🌐 Auto-detects user region via IP for locale defaults

## 🛠️ Tech Stack

**Backend**
- Python 3 + Flask
- Flask-CORS
- Google Gemini API (`gemini-flash-latest`)

**Frontend**
- Vanilla HTML5, CSS3, JavaScript (single-page app)
- Web Speech API (`SpeechRecognition`)
- MediaRecorder API (audio capture)
- Leaflet.js (map/location display)
- Google Fonts (Syne, JetBrains Mono)

## 📁 Project Structure

```
LangID/
└── multi-askanything/
    ├── main.py         # Flask backend — Gemini API integration & all routes
    ├── index.html       # Frontend single-page app
    └── .env             # Environment variables (DO NOT COMMIT — see below)
```

## 🔌 API Endpoints

| Route | Method | Description |
|---|---|---|
| `/analyze` | POST | Analyze recorded audio → language, transcription, translation, emotion, etc. |
| `/translate` | POST | Translate given text into a target language |
| `/detect-text` | POST | Detect language of typed/pasted text |
| `/zara` | POST | Query the ZARA AUCE college helpdesk assistant |
| `/ask` | POST | General-purpose AI assistant (no topic restriction) |
| `/languages` | GET | List of supported languages with metadata |
| `/college-kb` | GET | Raw AUCE knowledge base (JSON) |
| `/health` | GET | Backend health/status check |

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- A Google Gemini API key ([Google AI Studio](https://aistudio.google.com/app/apikey))

### Setup

```bash
git clone https://github.com/<your-username>/LangID.git
cd LangID/multi-askanything

# Install dependencies
pip install flask flask-cors

# Set your API key (create a .env file — see below)
echo "GEMINI_API_KEY=your_api_key_here" > .env

# Run the backend
python3 main.py
```

The server starts at **http://localhost:1000**. Open `index.html` in your browser (or serve it via a local server) to use the app.

### ⚠️ Security Note

This project's `main.py` includes a hardcoded fallback API key and an `.env` file with a real key. **Before pushing to GitHub:**
1. Remove the hardcoded key from `main.py` — keep only `os.environ.get("GEMINI_API_KEY")` with no fallback value.
2. Delete or exclude `.env` from version control.
3. Rotate/regenerate the exposed key in Google AI Studio.
4. Add a `.gitignore` with:
   ```
   .env
   __pycache__/
   *.pyc
   ```

## 📌 Project Context

LangID was developed as a capstone project. My role was **Frontend/UI Development** — building the real-time recording interface, results dashboard, ZARA assistant UI, and multilingual interaction flows.

## 📄 License

For academic/portfolio use.

## 🙋 Author

**Naramala Pavan Kumar**
[GitHub](https://github.com/NaramalaPavanaKumar)
