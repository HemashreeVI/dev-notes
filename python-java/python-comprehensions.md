# Python comprehensions and generators

```python
squares = [x * x for x in range(10)]                 # list
evens   = [x for x in nums if x % 2 == 0]            # filter
index   = {u.id: u for u in users}                   # dict
uniq    = {w.lower() for w in words}                 # set
flat    = [x for row in matrix for x in row]         # nested, outer loop first
total   = sum(x * x for x in range(10**7))           # generator: no big list in memory
```

**Generator functions** stream data lazily:

```python
def read_lines(path):
    with open(path) as f:
        for line in f:
            yield line.rstrip("\n")
```

**Rule:** if a comprehension needs more than one `if` or two `for`s, a normal loop is clearer.
