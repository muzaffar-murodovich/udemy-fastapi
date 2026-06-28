# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Coursework for "FastAPI - The Complete Course" by Eric Roby. It is **not** a single
application but a series of progressively-built reference projects. Each top-level
`Project N` folder is an independent, self-contained snapshot of the same TodoApp at a
later stage of the course — they intentionally duplicate code and diverge incrementally.
Treat each project as its own codebase; do not share or deduplicate code across them.

## Per-project guides

Each folder has its own `CLAUDE.md` with the specifics for that stage. Read the one for
the folder you're working in:

- [`Project 1/CLAUDE.md`](Project%201/CLAUDE.md) — in-memory Books API (`Body`, path/query params).
- [`Project 2/CLAUDE.md`](Project%202/CLAUDE.md) — Books API with Pydantic models & validation.
- [`Project 3/CLAUDE.md`](Project%203/CLAUDE.md) — TodoApp: SQLAlchemy + JWT auth (no Alembic, no phone_number).
- [`Project 3.5/CLAUDE.md`](Project%203.5/CLAUDE.md) — TodoApp + `phone_number` column + Alembic.
- [`Project 4/CLAUDE.md`](Project%204/CLAUDE.md) — TodoApp + pytest suite.
- [`Project 5/CLAUDE.md`](Project%205/CLAUDE.md) — TodoApp + Jinja2 frontend (static/templates).
- [`PythonRefresher/CLAUDE.md`](PythonRefresher/CLAUDE.md) — standalone Python practice scripts.

## Cross-cutting facts

- **Directory matters.** Paths in the TodoApp code are relative to the current working
  directory. Run `uvicorn`, `pytest`, and `alembic` from the locations noted in each
  project's guide, never from inside `TodoApp`.
- `Database Scripts/` holds raw MySQL / PostgreSQL setup scripts used by the course; the
  default DB in code is local SQLite.
- One shared environment: `pip install -r requirements.txt` covers all projects.
