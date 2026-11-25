# Two pointers

Use on **sorted arrays** or when comparing both ends. Turns O(n²) pair searches into O(n).

```python
def two_sum_sorted(nums, target):
    l, r = 0, len(nums) - 1
    while l < r:
        s = nums[l] + nums[r]
        if s == target:
            return l, r
        if s < target:
            l += 1          # need bigger
        else:
            r -= 1          # need smaller
    return None
```

**Also fits:** reverse a string, remove duplicates in place (slow/fast pointer), container with most water, 3Sum (sort + fix one + two pointers).

**Signal words:** "sorted", "pair", "in place", "palindrome".
