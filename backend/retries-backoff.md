# Retries with exponential backoff and jitter

Retry only what can succeed later: timeouts, 429, 502, 503, 504. Never retry 400/401/404.

```python
import random, time

def call_with_retry(fn, attempts=5, base=0.2, cap=5.0):
    for i in range(attempts):
        try:
            return fn()
        except TransientError:
            if i == attempts - 1:
                raise
            delay = min(cap, base * 2 ** i)
            time.sleep(random.uniform(0, delay))     # "full jitter"
```

**Why jitter?** Without it, every client retries at the same instant and knocks the service over again.

**Also**
- Only retry idempotent operations (or use idempotency keys).
- Put a total deadline on the whole call.
- Add a **circuit breaker**: after many failures, stop calling for a while and fail fast.
