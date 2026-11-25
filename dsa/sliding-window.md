# Sliding window

For **contiguous** subarrays/substrings with a condition. Grow the right edge, shrink the left when the window breaks the rule. O(n).

```python
def longest_unique_substring(s):
    seen, left, best = {}, 0, 0
    for right, ch in enumerate(s):
        if ch in seen and seen[ch] >= left:
            left = seen[ch] + 1          # jump past the duplicate
        seen[ch] = right
        best = max(best, right - left + 1)
    return best
```

**Template**
1. Expand `right`, add `s[right]` to the window state.
2. While the window is invalid, remove `s[left]`, `left += 1`.
3. Update the answer.

**Signal words:** "longest/shortest substring", "subarray with sum", "at most k distinct".
