# Health checks

Two different questions:

| Probe | Question | On failure |
|---|---|---|
| **liveness** | is the process stuck? | restart it |
| **readiness** | can it serve traffic right now? | stop sending requests |

```python
@app.get("/health/live")
def live():
    return {"status": "ok"}                 # no dependencies: just "I'm running"

@app.get("/health/ready")
def ready():
    db.execute("SELECT 1")                  # check what you need to serve
    return {"status": "ready"}
```

**Gotcha:** don't check the database in *liveness*. If the DB blips, every replica restarts at once and makes the outage worse.
