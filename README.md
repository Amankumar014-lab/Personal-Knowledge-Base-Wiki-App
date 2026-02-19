# Personal Knowledge Base (PKB) — Internship Project

This is a beginner-friendly Personal Knowledge Base / Wiki built with Flask and Google Firestore.

Features
- Create, edit, view, delete articles
- Version history for every edit (restore older versions)
- Internal wiki links using [[Article Title]] syntax
- Tags (multiple per article) and tag filtering
- Simple search (title/content/tags)
- Responsive, minimal UI

Quick setup
1. Create a Python virtualenv and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\activate on Windows
pip install -r requirements.txt
```

2. Firebase credentials:
- Place your Firebase Admin SDK JSON in the project root named `serviceAccountKey.json`, or set `FIREBASE_CREDENTIALS` env var to its path.

3. Run locally:

```bash
export FLASK_APP=app.py
flask run
```

On Windows (PowerShell):

```powershell
$env:FLASK_APP = 'app.py'
flask run
```

Notes
- Firestore must be accessible with provided credentials. For local testing, you can use the Firestore emulator (adjust `firebase-admin` init accordingly).
- The internal link parser turns `[[Title]]` into `/articles/view?title=Title` links. The view route resolves by title when possible.
- Versioning: on every edit the previous content is stored in the `versions` collection with an incrementing `version_no`. Restoring a version will also save the current content as a new version.

Security
- This demo is intended for learning. In production, sanitize HTML, add authentication, rate-limiting, and stricter validation.
