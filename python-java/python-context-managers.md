# Python context managers

`with` guarantees cleanup, even when an exception is raised.

```python
with open("data.csv") as f:          # file always closed
    rows = f.readlines()

with db.transaction():               # commit on success, rollback on exception
    db.execute(...)
```

**Write your own** with `contextlib`:

```python
import time
from contextlib import contextmanager

@contextmanager
def timer(name):
    start = time.perf_counter()
    try:
        yield
    finally:
        print(f"{name}: {time.perf_counter() - start:.3f}s")

with timer("load"):
    load_everything()
```

Java's equivalent is try-with-resources on anything `AutoCloseable`.
