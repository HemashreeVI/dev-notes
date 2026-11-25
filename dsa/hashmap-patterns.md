# Hashmap patterns

**Seen-before (two sum, unsorted):**

```python
def two_sum(nums, target):
    idx = {}
    for i, x in enumerate(nums):
        if target - x in idx:
            return idx[target - x], i
        idx[x] = i
```

**Counting:**

```python
from collections import Counter
Counter("anagram") == Counter("nagaram")     # anagram check
Counter(words).most_common(3)                # top 3
```

**Grouping by a key:**

```python
from collections import defaultdict
groups = defaultdict(list)
for w in words:
    groups["".join(sorted(w))].append(w)     # group anagrams
```

Trade O(n) memory for O(1) lookups. If you're nesting loops to "find a match", a hashmap is usually the fix.
