# arora-ai
# 🎓 StudyBuddy AI

A Streamlit + Google Gemini study assistant.

## Features
- **Explain**: upload PDF, Word, PowerPoint, Excel, text, image, audio or video and get an easy explanation (3 styles)
- **Lectures**: record in the browser or upload audio, then get a short summary of the important points
- **Notes**: friendly study notes and a cheat-sheet, downloadable as Markdown
- **Roadmap**: enter a field, level (Beginner / Intermediate / Advanced / PhD) and time, then get a full plan
- **Visuals**: AI images, plus a cartoon explainer (cartoon pictures with a narrator voice)
- **Exam**: up to 150 MCQs (default 100) with answer review, then a surprise light-up and an appreciation token

## Run locally
1. Install Python 3.10+.
2. Get a free API key at https://aistudio.google.com/apikey
3. In this folder run:
   ```bash
   pip install -r requirements.txt
   streamlit run app.py
   ```
4. Paste your key into the sidebar (or put `GEMINI_API_KEY = "your-key"` in `.streamlit/secrets.toml`).

## Push to GitHub
1. Create a free account at github.com and click **New repository** (name it `studybuddy-ai`, set it Public, don't add a README).
2. In this folder run:
   ```bash
   git init
   git add app.py README.md requirements.txt
   git commit -m "StudyBuddy AI"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/studybuddy-ai.git
   git push -u origin main
   ```
3. **Never commit your API key.** Keep it in Streamlit secrets only.

## Deploy on Streamlit Community Cloud (free)
1. Go to https://share.streamlit.io and sign in with GitHub.
2. Click **Create app**, pick your repo, branch `main`, and main file `app.py`.
3. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key-here"
   ```
4. Click **Deploy**. When it finishes you get a public link.

## Optional: bigger uploads
Streamlit allows 200 MB per file by default. To raise it, create `.streamlit/config.toml`:
```toml
[server]
maxUploadSize = 1000
```

## Honest limits
- **Not unlimited:** Gemini's free tier has per-minute and daily limits, so very heavy use shows a quota error. Wait and retry. The app retries rate-limit errors automatically.
- **Long files:** Gemini Flash reads very large inputs, but extremely long audio or video can be slow or hit the daily limit.
- **Videos:** The cartoon explainer is an illustrated story with narration, not an MP4 file. Real AI video generation is not free.
- **Images:** The free image model may be unavailable or limited on some accounts. If so, the app shows a message and everything else still works.
- **Data:** Nothing is stored on a server. Material, notes and exams last only for the browser session, so use the Download buttons.
- **Accuracy:** AI can make mistakes. Check important facts with your teacher or textbook.

## If something breaks
- The model name is set at the top of `app.py` (`MODEL` and `IMAGE_MODEL`). If Google renames a model, change it there.
