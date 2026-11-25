# Complexity cheat sheet

**What fits in ~1 second** (about 10⁸ simple operations):

| n | Max complexity |
|---|---|
| ≤ 10 | O(n!) |
| ≤ 20 | O(2ⁿ) |
| ≤ 500 | O(n³) |
| ≤ 5,000 | O(n²) |
| ≤ 10⁶ | O(n log n) |
| ≤ 10⁸ | O(n) |

**Common operations**

| Structure | Access | Search | Insert/Delete |
|---|---|---|---|
| Array / list | O(1) | O(n) | O(n) (end: O(1)) |
| Hash map / set | n/a | O(1) avg | O(1) avg |
| Heap | min O(1) | O(n) | O(log n) |
| Balanced BST / TreeMap | O(log n) | O(log n) | O(log n) |

Read the constraints first: they tell you which algorithm the problem expects.
