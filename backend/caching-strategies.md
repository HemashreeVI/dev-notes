# Caching strategies

**Cache-aside** (most common):

```python
def get_user(uid):
    if (u := redis.get(f"user:{uid}")):
        return json.loads(u)
    u = db.fetch_user(uid)
    redis.setex(f"user:{uid}", 300, json.dumps(u))   # 5 min TTL
    return u
```

On update: write the DB, then **delete** the cache key (don't update it, to avoid races).

| Pattern | Write path |
|---|---|
| cache-aside | app writes DB, invalidates cache |
| write-through | app writes cache, cache writes DB synchronously |
| write-behind | cache writes DB later (fast, can lose data) |

**Gotchas**
- **Stampede:** a hot key expires and 1,000 requests hit the DB. Use a lock or early random refresh.
- Always set a TTL, so a missed invalidation heals itself.
