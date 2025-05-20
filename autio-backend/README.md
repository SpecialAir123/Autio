# Autio Backend MVP

This repository contains the minimal scaffold for the Autio backend MVP, built using FastAPI. It provides user authentication and a foundation for an AI-powered chat endpoint for car recommendations.

## Prerequisites

* Python 3.8+
* `pip` package manager
* (Optional) [virtualenv](https://virtualenv.pypa.io/) or `venv` for isolating dependencies

## Installation

1. **Clone the repository**

   ```bash
   git clone <your-repo-url> autio-backend
   cd autio-backend
   ```

2. **Create and activate a virtual environment**

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate      # macOS/Linux
   # .venv\Scripts\activate     # Windows PowerShell
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   Create a file named `.env` in the project root with:

   ```dotenv
   DATABASE_URL=sqlite+aiosqlite:///./autio.db
   JWT_SECRET=your-jwt-secret
   OPENAI_API_KEY=sk-your-openai-key
   ```

## Project Structure

```text
autio-backend/
├── .env                # Environment variables
├── requirements.txt    # Python dependencies
├── main.py             # FastAPI application entrypoint
├── db.py               # Database engine & session setup
├── models.py           # SQLAlchemy models (User table)
├── schemas.py          # Pydantic request/response schemas
└── auth.py             # Password hashing & JWT utilities
```

## Quick Start

1. **Run the server**

   ```bash
   uvicorn main:app --reload
   ```

2. **Test the root endpoint**
   Open your browser or use `curl`:

   ```bash
   curl http://localhost:8000/
   ```

   You should see:

   ```json
   {"message":"Autio backend is up and running!"}
   ```

## Next Steps

1. **Database Setup** (`db.py`)

   * Initialize async engine & session.
   * Create database tables on startup.

2. **User Model** (`models.py`)

   * Define `User` table with `id`, `email`, and `hashed_password` columns.

3. **Schemas** (`schemas.py`)

   * Define Pydantic models for user signup, login token, and chat messages.

4. **Authentication** (`auth.py`)

   * Implement password hashing (bcrypt) and JWT creation/verification.
   * Create `/signup` and `/token` routes in `main.py`.

5. **Chat Endpoint** (`main.py`)

   * Add `/chat` route that forwards user messages to OpenAI’s ChatCompletion API.
   * Protect using JWT authentication middleware.
