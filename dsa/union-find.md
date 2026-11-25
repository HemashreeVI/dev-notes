# Union-Find (Disjoint Set Union)

Tracks which items are in the same group, with near-O(1) merge and lookup.

```python
class DSU:
    def __init__(self, n):
        self.parent, self.size = list(range(n)), [1] * n
    def find(self, x):
        while self.parent[x] != x:
            self.parent[x] = self.parent[self.parent[x]]   # path compression
            x = self.parent[x]
        return x
    def union(self, a, b):
        ra, rb = self.find(a), self.find(b)
        if ra == rb:
            return False                                   # already connected
        if self.size[ra] < self.size[rb]:
            ra, rb = rb, ra
        self.parent[rb] = ra                               # union by size
        self.size[ra] += self.size[rb]
        return True
```

**Uses:** number of connected components, detecting a cycle in an undirected graph, Kruskal's minimum spanning tree, "accounts merge".
