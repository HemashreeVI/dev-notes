# BFS: shortest path in unweighted graphs

Explore level by level with a queue. The first time you reach a node is via a shortest path.

```python
from collections import deque

def shortest_path(grid, start, goal):
    rows, cols = len(grid), len(grid[0])
    q, seen = deque([(start, 0)]), {start}
    while q:
        (r, c), d = q.popleft()
        if (r, c) == goal:
            return d
        for dr, dc in ((1,0),(-1,0),(0,1),(0,-1)):
            nr, nc = r + dr, c + dc
            if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 0 and (nr, nc) not in seen:
                seen.add((nr, nc))            # mark when ADDING, not when popping
                q.append(((nr, nc), d + 1))
    return -1
```

**Multi-source BFS:** start with all sources in the queue (rotting oranges, distance to nearest 0).
