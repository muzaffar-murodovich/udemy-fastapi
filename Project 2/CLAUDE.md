# CLAUDE.md — Project 2 (Books API with Pydantic)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

Single-file FastAPI app (`books2.py`), the evolution of Project 1: still an in-memory list,
but now uses Pydantic `BaseModel` request models, `Field` validation, and `Path`/`Query`
constraints. No database.

## Run

From inside this folder:

```bash
uvicorn books2:app --reload
```

Interactive docs at `/docs`.
