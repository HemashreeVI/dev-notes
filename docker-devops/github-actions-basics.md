# GitHub Actions basics

`.github/workflows/ci.yml`:

```yaml
name: CI
on:
  push: { branches: [main] }
  pull_request:
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: "3.12", cache: pip }
      - run: pip install -r requirements.txt
      - run: pytest -q
```

**Concepts:** workflow (file) → jobs (run in parallel on separate machines) → steps (run in order on one machine).

**Tips**
- `needs: test` makes one job wait for another.
- Secrets: `${{ secrets.API_KEY }}`; they're masked in logs and unavailable to PRs from forks.
- `workflow_dispatch:` adds a "Run workflow" button.
