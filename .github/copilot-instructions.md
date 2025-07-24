# Copilot Instructions for Mergington High School Activities API

## Project Overview
- This is a simple FastAPI web application for managing extracurricular activities at Mergington High School.
- The backend is in `src/app.py` and exposes REST endpoints for listing activities and signing up students.
- The frontend is a static site in `src/static/` (HTML, CSS, JS) and interacts with the backend via fetch requests.
- All data is stored in-memory (Python dicts); no database is used. Data resets on server restart.

## Key Components
- `src/app.py`: FastAPI app, in-memory data, API endpoints, static file serving.
- `src/static/index.html`: Main UI for students to view and sign up for activities.
- `src/static/app.js`: Fetches activities, handles sign-up form, updates UI.
- `requirements.txt`: Python dependencies (FastAPI, Uvicorn).

## Developer Workflows
- **Install dependencies:**
  ```bash
  pip install -r requirements.txt
  ```
- **Run the server:**
  ```bash
  python src/app.py
  # or
  uvicorn src.app:app --reload
  ```
- **Access the app:**
  - Open `http://localhost:8000/static/index.html` for the UI
  - API docs: `http://localhost:8000/docs`

## API Endpoints
- `GET /activities` — List all activities and participants
- `POST /activities/{activity_name}/signup?email=...` — Sign up a student by email

## Patterns & Conventions
- Activity names and student emails are unique identifiers.
- No persistent storage; all state is lost on restart.
- Static files are served from `/static` via FastAPI's `StaticFiles`.
- Frontend JS expects API to be available at the same host/port as static files.
- No authentication or authorization is implemented.

## Example Data Model
```python
activities = {
  "Chess Club": {
    "description": "...",
    "schedule": "...",
    "max_participants": 12,
    "participants": ["michael@mergington.edu"]
  },
  ...
}
```

## Tips for AI Agents
- When adding new features, keep the in-memory data model and statelessness in mind.
- For new endpoints, follow the FastAPI style in `app.py`.
- For UI changes, update both `index.html` and `app.js` as needed.
- Keep the developer workflow simple: no build steps, just run the Python server.

---
For questions about conventions or unclear patterns, ask for clarification or check `src/README.md` for more details.
