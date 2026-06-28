# CLAUDE.md — Project 3.5 (TodoApp + Alembic)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

Same TodoApp as [Project 3](../Project%203/CLAUDE.md) with two additions:

- A `phone_number` column on `Users` (`models.py`).
- **Alembic** migrations under `TodoApp/alembic/`, config in `TodoApp/alembic.ini`
  (`sqlalchemy.url = sqlite:///./todosapp.db`). The existing migration adds the
  `phone_number` column.

The architecture (main / database / models / routers, JWT+bcrypt auth) is otherwise
identical to Project 3 — see that guide.

## Run

From **this folder** (parent of `TodoApp`):

```bash
uvicorn TodoApp.main:app --reload
```

## Alembic

Run from `TodoApp/` (the folder containing `alembic.ini`):

```bash
alembic revision -m "message"   # autogenerate not configured; edit the migration by hand
alembic upgrade head
alembic downgrade -1
```
