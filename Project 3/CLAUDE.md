# CLAUDE.md — Project 3 (TodoApp: DB + Auth)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

First full TodoApp: FastAPI + SQLAlchemy + JWT auth. **No Alembic and no `phone_number`
column yet** (those arrive in Project 3.5).

## Architecture (`TodoApp/`)

- `main.py` — creates the app, runs `Base.metadata.create_all(bind=engine)` on startup,
  and wires routers via `app.include_router(...)`.
- `database.py` — SQLAlchemy `engine`, `SessionLocal`, `Base`. Default DB is local SQLite
  (`sqlite:///./todosapp.db`).
- `models.py` — `Users` and `Todos` (`Todos.owner_id` → `Users.id`).
- `routers/` — `auth`, `todos`, `admin`, `users`. Each defines its own
  `APIRouter(prefix=..., tags=...)` and a local `get_db` dependency.
- Auth: JWT (`python-jose`) + bcrypt (`passlib`). `SECRET_KEY`, `ALGORITHM`, and
  `get_current_user` live in `routers/auth.py`. The token carries `sub`, `id`, `role`;
  admin routes require `role == 'admin'`. The secret key is hardcoded (course code).
- Dependency pattern: `db_dependency = Annotated[Session, Depends(get_db)]` and
  `user_dependency = Annotated[dict, Depends(get_current_user)]`.

## Run

Paths and relative imports require running from **this folder** (the parent of `TodoApp`),
not from inside `TodoApp`. The SQLite file is created in the cwd.

```bash
uvicorn TodoApp.main:app --reload
```
