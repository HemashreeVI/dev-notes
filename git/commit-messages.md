# Writing good commit messages

```text
Add retry with backoff to payment client          <- summary, imperative, <= 50 chars

Payment provider returns 503 during deploys. Retry  <- body: WHY, wrapped at 72
up to 3 times with exponential backoff (200ms base)
so checkout doesn't fail for users.

Closes #42
```

**Rules**
- Imperative mood: "Add", "Fix", "Remove", not "Added"/"Fixes".
- The summary completes the sentence "If applied, this commit will ___".
- Body explains *why*; the diff already shows *what*.

**Conventional Commits** (optional prefix, useful for changelogs): `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`.
