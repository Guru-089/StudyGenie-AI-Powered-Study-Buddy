🎓 StudyGenie Pro — AI-Powered Study Assistant
StudyGenie Pro is a Streamlit-based learning assistant that uses the Groq API to help students study. It brings AI question answering, text/PDF summarization, and multiple-choice question generation together in one interface.
✨ Features
- 💬 AI Tutor: Ask academic questions and receive AI-generated explanations.
- 📄 Smart Summarizer: Summarize pasted text or text extracted from PDF documents.
- 📝 MCQ Generator: Generate five practice multiple-choice questions for a topic.
- 🎨 Custom UI: Dark neon theme with animated gradients, glassmorphism cards, and responsive Streamlit styling.
- 🗂️ Study-session hooks: The app calls session-storage helper functions to record questions, summaries, and quiz topics.
- 🔐 Login UI: Includes login and sign-up screens as currently implemented in the app.
🧰 Tech Stack
- Python
- Streamlit
- Groq API (llama-3.1-8b-instant)
- pypdf
- pandas
- CSS
- Firebase/Firestore helper interface (currently mocked in firebase_config.py)
📁 Project Structure
.
├── app.py
├── style.css
├── firebase_config.py
├── requirements.txt
├── vercel.json
└── README.md
🚀 Run Locally
1. Clone the repository
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd YOUR-REPOSITORY
Replace the URL and folder name with your GitHub repository details.
2. Create and activate a virtual environment (recommended)
Windows
python -m venv .venv
.venv\Scripts\activate
macOS/Linux
python3 -m venv .venv
source .venv/bin/activate
3. Install dependencies
pip install -r requirements.txt
4. Configure your Groq API key
Create a .streamlit/secrets.toml file in the project root:
GROQ_API_KEY = "your_groq_api_key_here"
Get an API key from the Groq developer console: https://console.groq.com/keys

Do not commit API keys or other secrets to GitHub.
5. Start the app
streamlit run app.py
Then open the local URL shown in the terminal (usually http://localhost:8501).
⚙️ Configuration Notes
- app.py reads GROQ_API_KEY from Streamlit secrets.
- firebase_config.py currently provides a mock database and mock session functions. Study sessions are not persisted by this mock implementation.
- The login/sign-up interface currently updates Streamlit session state; it is not production-grade authentication and does not verify credentials.
- vercel.json configures a Vercel Python build and routes requests to app.py. Streamlit apps generally need a Streamlit-compatible hosting setup, so verify deployment compatibility before relying on this Vercel configuration.
🛡️ Security & Deployment
- Never upload .streamlit/secrets.toml, .env, service-account JSON files, or API keys.
- Add these entries to .gitignore if they exist:
.venv/
__pycache__/
*.py[cod]
.env
.streamlit/secrets.toml
serviceAccountKey.json
- For a public demo, use a hosting provider that supports Streamlit and configure GROQ_API_KEY as a server-side secret.
- Before production use, implement real authentication, validate uploads and user input, and replace the mock database with a properly secured database integration.
🧪 Troubleshooting
GROQ_API_KEY is missing or invalid
- Check that .streamlit/secrets.toml exists and contains the correct key.
- Confirm the key is active and that your hosting platform has the secret configured.
Dependencies fail to install
- Upgrade pip and retry:python -m pip install --upgrade pip
  pip install -r requirements.txt
PDF summary is empty
- Make sure the PDF contains selectable text. Scanned/image-only PDFs may require OCR, which is not currently included.
🗺️ Future Improvements
- Implement real user authentication and Google sign-in.
- Connect Firebase/Firestore for persistent study history.
- Add quiz answer options, scoring, and explanations.
- Improve PDF handling for multi-page documents and scanned PDFs.
- Add tests, logging, and deployment documentation.
