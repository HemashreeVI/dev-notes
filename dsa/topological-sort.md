# Topological sort

Order tasks so every dependency comes first. Only possible if there's no cycle.

**Kahn's algorithm (BFS on in-degrees):**

```python
from collections import deque, defaultdict

def topo_order(n, edges):            # edge (a, b) means a before b
    graph, indeg = defaultdict(list), [0] * n
    for a, b in edges:
        graph[a].append(b)
        indeg[b] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    order = []
    while q:
        u = q.popleft()
        order.append(u)
        for v in graph[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return order if len(order) == n else []   # [] => cycle
```

**Real uses:** build systems, course schedules, package installs, Airflow DAGs.
