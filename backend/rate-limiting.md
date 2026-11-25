# Rate limiting algorithms

| Algorithm | How | Trade-off |
|---|---|---|
| Fixed window | count per minute, reset at :00 | simple; allows 2x burst at the boundary |
| Sliding window | count over the last 60 s | smoother; more bookkeeping |
| Token bucket | tokens refill at rate r, request costs 1, max b | allows short bursts up to b; most common |
| Leaky bucket | queue drained at a fixed rate | smooth output; adds latency |

Token bucket in Redis (per user), sketched:

```text
tokens = min(capacity, tokens + (now - last) * rate)
if tokens >= 1: tokens -= 1, allow   else: reject 429
```

Run it as a Lua script so the read-modify-write is atomic.

**Respond with** `429` plus `Retry-After` and `X-RateLimit-Remaining` headers.
