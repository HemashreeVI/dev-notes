# Prefix sums

Precompute running totals so any range sum is O(1).

```python
prefix = [0]
for x in nums:
    prefix.append(prefix[-1] + x)
range_sum = prefix[r + 1] - prefix[l]      # sum of nums[l..r]
```

**Subarray sum equals k** (works with negatives) using a hashmap of prefix counts:

```python
from collections import defaultdict
def subarray_sum(nums, k):
    count, total, seen = 0, 0, defaultdict(int)
    seen[0] = 1
    for x in nums:
        total += x
        count += seen[total - k]
        seen[total] += 1
    return count
```

2D version: `P[i+1][j+1] = M[i][j] + P[i][j+1] + P[i+1][j] - P[i][j]`.
