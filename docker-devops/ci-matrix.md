# CI matrix builds

Test many versions with one job definition.

```yaml
jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      fail-fast: false
      matrix:
        os: [ubuntu-latest, windows-latest]
        python: ["3.10", "3.11", "3.12"]
        exclude:
          - { os: windows-latest, python: "3.10" }
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: "${{ matrix.python }}" }
      - run: pytest -q
```

That's 5 jobs running in parallel. `fail-fast: false` lets the others finish when one fails, so you see every broken combination at once.
