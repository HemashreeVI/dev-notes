# Heaps and top-k

Python's `heapq` is a **min-heap**.

```python
import heapq

# k largest in O(n log k): keep a min-heap of size k
def top_k(nums, k):
    h = []
    for x in nums:
        heapq.heappush(h, x)
        if len(h) > k:
            heapq.heappop(h)          # drop the smallest
    return sorted(h, reverse=True)

heapq.nlargest(3, nums)               # built-in shortcut
heapq.heappush(h, -x)                 # max-heap trick: negate
heapq.heappush(h, (priority, i, item))  # tuples; i breaks ties
```

**Patterns:** k closest points, merge k sorted lists, median of a stream (two heaps), task scheduling, Dijkstra.
