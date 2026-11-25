# Design: URL shortener

**Requirements:** shorten a URL, redirect fast, ~100:1 reads to writes.

**API**
- `POST /urls {long_url}` → `{code: "aZ3kP9"}`
- `GET /aZ3kP9` → `301/302` to the long URL

**Code generation:** take a unique ID from a counter (DB sequence, or ID blocks handed to each server) and base62-encode it. 7 chars of `[0-9a-zA-Z]` = 62⁷ ≈ 3.5 trillion codes. No collisions to check.

**Storage:** `code → long_url, created_at, owner`. A key-value store or SQL with the code as primary key.

**Read path:** cache hot codes in Redis; most traffic never hits the DB. Put a CDN or edge in front for popular links.

**Extras:** 302 (not 301) if you need click analytics; rate-limit creation; scan URLs for malware.
