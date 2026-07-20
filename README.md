# Todo API

A simple CRUD API for managing a to-do list, built with **FastAPI** (Python). Supports create, read, update, and delete operations on tasks, with in-memory storage and interactive Swagger UI documentation.

Built as part of the FlyRank Backend AI Engineering internship — Week 2, Assignment BE-01 (*Build your first CRUD API*).

## Tech Stack

- Python 3.10+
- FastAPI
- Uvicorn (ASGI server)

## Setup & Run

1. Clone the repo:
```bash
   git clone https://github.com/SaharGhaffar7/todo-api.git
   cd todo-api/py-version
```

2. Create and activate a virtual environment:
```bash
   python -m venv venv
   venv\Scripts\activate.bat
```

3. Install dependencies:
```bash
   pip install fastapi uvicorn
```

4. Run the server:
```bash
   uvicorn main:app --reload
```

5. The API will be available at `http://localhost:8000`, and the interactive Swagger docs at `http://localhost:8000/docs`.

## Endpoints

| Method | Endpoint         | Description                          | Success Code | Error Codes |
|--------|------------------|---------------------------------------|---------------|--------------|
| GET    | `/`              | API info (name, version, endpoints)   | 200           | –            |
| GET    | `/health`        | Health check                          | 200           | –            |
| GET    | `/tasks`         | List all tasks                        | 200           | –            |
| GET    | `/tasks/{id}`    | Get a single task by ID                | 200           | 404          |
| POST   | `/tasks`         | Create a new task                     | 201           | 400          |
| PUT    | `/tasks/{id}`    | Update a task's title and/or status   | 200           | 400, 404     |
| DELETE | `/tasks/{id}`    | Delete a task                         | 204           | 404          |

## Example Request

Creating a new task:

```bash
curl -i -X POST http://localhost:8000/tasks -H "Content-Type: application/json" -d "{\"title\":\"Buy milk\"}"
```

Response:HTTP/1.1 201 Created
content-type: application/json

{"id":4,"title":"Buy milk","done":false}

## Data Model

Each task has the following shape:

```json
{
  "id": 1,
  "title": "Buy groceries",
  "done": false
}
```

Data is stored **in-memory only** — it resets whenever the server restarts (no database is used in this stage).

## Project Structure

todo-api/
└── py-version/
├── main.py
└── venv/

## Development Notes

This project was built stage by stage, with one Git commit per stage:

- Stage 0: Hello server
- Stage 1: Root and health endpoints
- Stage 2: Read endpoints with 404 handling
- Stage 3: Create endpoint with validation
- Stage 4: Update and delete endpoints (full CRUD complete)
- Stage 5: Swagger UI tested
