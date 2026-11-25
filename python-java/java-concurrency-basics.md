# Java concurrency basics

**Use an executor, not raw threads:**

```java
ExecutorService pool = Executors.newFixedThreadPool(8);
Future<Integer> f = pool.submit(() -> compute());
int result = f.get(2, TimeUnit.SECONDS);
pool.shutdown();
```

**Java 21+: virtual threads** for lots of blocking I/O:

```java
try (var exec = Executors.newVirtualThreadPerTaskExecutor()) {
    urls.forEach(u -> exec.submit(() -> fetch(u)));
}
```

**Shared state**
- `AtomicInteger`, `ConcurrentHashMap` for simple counters and maps.
- `synchronized` or `ReentrantLock` for compound actions (check-then-act).
- Prefer immutability: no shared mutable state, no race.

**Classic bug:** `if (!map.containsKey(k)) map.put(k, v)` is not atomic. Use `map.putIfAbsent(k, v)` or `computeIfAbsent`.
