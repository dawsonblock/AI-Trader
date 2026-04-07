# AI-Trader service/

This directory contains the runnable application code:

- `server/` — FastAPI backend
- `frontend/` — Vite/React frontend

## Local setup

### Backend

```bash
cd /home/runner/work/AI-Trader/AI-Trader
python -m venv .venv
source .venv/bin/activate
pip install -r /home/runner/work/AI-Trader/AI-Trader/service/requirements.txt
cp .env.example .env
cd /home/runner/work/AI-Trader/AI-Trader/service/server
uvicorn main:app --reload --port 8000
```

Notes:
- leave `DATABASE_URL` empty to use the SQLite fallback database
- set `DATABASE_URL` to a PostgreSQL connection string to use PostgreSQL instead
- the backend currently expects to run from `service/server` because imports are not package-relative

### Frontend

```bash
cd /home/runner/work/AI-Trader/AI-Trader/service/frontend
npm ci
npm run dev
```

### Build frontend assets for backend serving

```bash
cd /home/runner/work/AI-Trader/AI-Trader/service/frontend
npm run build
```

When the frontend build output exists in `service/frontend/dist`, the backend serves it from `/`.
