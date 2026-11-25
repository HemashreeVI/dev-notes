# Exceptions: good habits (Python and Java)

**Catch specific exceptions:**

```python
try:
    user = repo.get(uid)
except UserNotFound:
    return 404
# not: except Exception: pass   <- hides real bugs
```

**Keep the cause when re-raising:**

```python
raise PaymentError("charge failed") from err
```

```java
throw new PaymentException("charge failed", e);   // pass e as the cause
```

**Rules**
- Fail fast on programmer errors; handle only what you can recover from.
- Map exceptions to HTTP responses in one place (FastAPI exception handlers, Spring `@ControllerAdvice`).
- Log once, at the boundary. Logging at every level creates duplicate stack traces.
- Clean up with `finally` / `with` / try-with-resources.
