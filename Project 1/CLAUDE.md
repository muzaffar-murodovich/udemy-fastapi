# CLAUDE.md — Project 1 (Books API)

See the [root CLAUDE.md](../CLAUDE.md) for repo-wide context.

Single-file FastAPI app (`books.py`) over an in-memory `BOOKS` list of dicts. No database,
no Pydantic models — the course intro to routes, path params, query params, and `Body()`
request bodies.

## Run

From inside this folder:

```bash
uvicorn books:app --reload
```

Interactive docs at `/docs`.
