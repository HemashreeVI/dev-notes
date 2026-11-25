# Python asyncio basics

Async helps with **waiting** (network, disk), not with CPU work.

```python
import asyncio, httpx

async def fetch(client, url):
    r = await client.get(url, timeout=10)
    return r.status_code

async def main(urls):
    async with httpx.AsyncClient() as client:
        results = await asyncio.gather(*(fetch(client, u) for u in urls))
    print(results)

asyncio.run(main(["https://example.com"] * 20))   # 20 requests concurrently
```

**Rules**
- Never call blocking code (`time.sleep`, `requests`) inside `async def`; it freezes the event loop. Use `await asyncio.sleep`, `httpx`, or `await asyncio.to_thread(fn)`.
- Limit concurrency with `asyncio.Semaphore(10)`.
- CPU-heavy work → `multiprocessing` or a process pool.
