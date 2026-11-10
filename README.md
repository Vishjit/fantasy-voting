# fantasy-voting

## Prerequisites

- Git
- Python 3.11+
- Node.js 18+ and npm
- Docker Desktop (running)

## Setup

### 1. Clone

```bash
git clone <REPO_URL>
cd fantasy-voting
```

### 2. Database (PostgreSQL via Docker)

From the repo root:

```bash
docker compose up -d
```

Check that it's running: `docker ps` (you should see the postgres container).

### 3. Backend (Django)

```bash
cd backend
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env            # skip if the repo has no .env.example yet
python manage.py migrate
python manage.py createsuperuser   # optional, for /admin
python manage.py runserver
```

Backend runs at http://localhost:8000

### 4. Frontend (React)

In a second terminal:

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at http://localhost:5173

## Daily Workflow

```bash
git pull
# if requirements.txt changed:  pip install -r requirements.txt
# if package.json changed:      npm install
# if new migrations were added: python manage.py migrate
```

## Rules

- Never commit `.env`, `venv/`, or `node_modules/`.
- Commit your migration files (`backend/<app>/migrations/`).
- Pull before you start work; branch for features (`git checkout -b feature/<name>`).
- NO BETTING features, ever.
