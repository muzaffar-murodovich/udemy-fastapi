# CLAUDE.md — Project 5 (TodoApp full-stack)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

Final stage: the [Project 4](../Project%204/CLAUDE.md) TodoApp (DB + JWT auth + Alembic +
tests) plus a **server-rendered frontend**.

## What's new vs Project 4

- `TodoApp/templates/` — Jinja2 templates (login, register, home, add/edit todo, layout,
  navbar). Routers render them with `Jinja2Templates(directory="TodoApp/templates")`.
- `TodoApp/static/` — Bootstrap CSS/JS, jQuery, custom `base.js`. Mounted in `main.py` as
  `StaticFiles(directory="TodoApp/static")` at `/static`.
- Routers gain page-rendering routes (e.g. `auth` has `/login-page`, `/register-page`)
  alongside the JSON API routes.
- `main.py` root `/` redirects to `/todos/todo-page`; `/healthy` is a health check.

## Run — directory matters

The `directory="TodoApp/static"` and `directory="TodoApp/templates"` paths are **relative
to the cwd**, so you must run from **this folder** (parent of `TodoApp`). Running from
inside `TodoApp` breaks static files and templates.

```bash
uvicorn TodoApp.main:app --reload
```

## Tests

Same setup as Project 4 — run from this folder:

```bash
pytest
pytest TodoApp/test/test_todos.py::test_read_all_authenticated
```

Alembic usage matches Project 3.5 (run from `TodoApp/`).
