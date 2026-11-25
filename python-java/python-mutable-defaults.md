# Python: mutable default arguments

Defaults are evaluated **once**, when the function is defined.

```python
def add(item, bucket=[]):      # one shared list for every call!
    bucket.append(item)
    return bucket

add(1)   # [1]
add(2)   # [1, 2]  <- surprise
```

**Fix:**

```python
def add(item, bucket=None):
    if bucket is None:
        bucket = []
    bucket.append(item)
    return bucket
```

Same trap with `dict`, `set`, and dataclass fields: use `field(default_factory=list)`.
