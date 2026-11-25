# Environment variables

```bash
export DATABASE_URL="postgres://localhost/app"   # set for this shell + children
echo "$DATABASE_URL"
env | grep DATABASE                              # list
unset DATABASE_URL
DEBUG=1 python app.py                            # set for one command only
```

Persist them in `~/.bashrc` / `~/.zshrc`, or per project in a `.env` file loaded by your app (python-dotenv, Spring profiles, Docker `env_file`).

```python
import os
url = os.environ["DATABASE_URL"]          # crash early if missing
debug = os.getenv("DEBUG", "0") == "1"    # optional with default
```

**Gotchas**
- Child processes inherit variables; parents never see changes from children.
- Keep `.env` in `.gitignore`. Commit a `.env.example` with fake values.
