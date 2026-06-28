# CLAUDE.md — Project 4 (TodoApp + Tests)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

Same TodoApp as [Project 3.5](../Project%203.5/CLAUDE.md) (DB + JWT auth + `phone_number` +
Alembic) with a **pytest suite** added under `TodoApp/test/`.

## Run

From **this folder** (parent of `TodoApp`):

```bash
uvicorn TodoApp.main:app --reload
```

## Tests

Run from **this folder** so the `TodoApp` package and its `..` relative imports resolve:

```bash
pytest                                                          # all tests
pytest TodoApp/test/test_todos.py                              # one file
pytest TodoApp/test/test_todos.py::test_read_all_authenticated # one test
```

How the test setup works (`TodoApp/test/utils.py`):

- Uses a **separate** SQLite DB (`testdb.db`) with a `StaticPool` and creates all tables.
- Overrides `get_db` and `get_current_user` via `app.dependency_overrides`
  (the fake user is `{'username': 'codingwithrobytest', 'id': 1, 'user_role': 'admin'}`).
- Provides `test_todo` / `test_user` pytest fixtures that insert a row, `yield`, then
  `DELETE FROM ...` to clean up.
- Each test module imports these with `from .utils import *` and sets the
  `app.dependency_overrides` at module import time.

Alembic usage matches Project 3.5 (run from `TodoApp/`).
