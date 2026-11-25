# Logging that helps at 3 a.m.

**Log structured JSON**, not free text, so you can filter by field:

```python
log.info("payment_failed", extra={"order_id": oid, "provider": "stripe", "status": 503})
```

```json
{"ts":"2026-11-25T10:01:02Z","level":"INFO","msg":"payment_failed","order_id":"A17","status":503,"trace_id":"9f2c"}
```

**Levels**
- `ERROR`: someone must act.
- `WARN`: unexpected but handled.
- `INFO`: business events (order placed, job finished).
- `DEBUG`: details, off in production.

**Rules**
- Include a request/trace ID in every line so one request can be followed across services.
- Never log passwords, tokens, or full card numbers.
- Log to stdout in containers; let the platform collect it.
