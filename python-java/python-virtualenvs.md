# Python virtual environments

One environment per project, so dependencies don't clash.

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
pip freeze > requirements.txt      # pin exact versions
deactivate
```

Add `.venv/` to `.gitignore`.

**Faster modern tool:** `uv`

```bash
uv venv
uv pip install -r requirements.txt
```

**Gotcha:** "module not found" while it's clearly installed usually means a different interpreter. Check `which python` and `python -m pip --version`, and always install with `python -m pip`.
