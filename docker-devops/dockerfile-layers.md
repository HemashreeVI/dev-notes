# Dockerfile layer caching

Each instruction is a cached layer. When one changes, every layer after it rebuilds. Order from "rarely changes" to "changes often".

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .                       # changes rarely
RUN pip install --no-cache-dir -r requirements.txt
COPY . .                                      # changes every commit
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0"]
```

If `COPY . .` came before `pip install`, every code change would reinstall all dependencies.

**Also:** add a `.dockerignore` (`.git`, `node_modules`, `.env`, `__pycache__`) so the build context stays small and secrets stay out.
