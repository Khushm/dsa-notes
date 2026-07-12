## Index: Graph

1. [Build Undirected Graph](#build-undirected-graph)
2. [Build Directed Graph](#build-directed-graph)
3. [Build Weighted Undirected Graph](#build-weighted-undirected-graph)
4. [Build Weighted Directed Graph](#build-weighted-directed-graph)
5. [Generic BFS](#generic-bfs)
6. [BFS for All Components](#bfs-for-all-components)
7. [Generic DFS](#generic-dfs)
8. [DFS for All Components](#dfs-for-all-components)
9. Note: [Adjacency List vs Adjacency Matrix Traversal](#adjacency-list-vs-adjacency-matrix)


---

## Notes

### Adjacency List vs Adjacency Matrix
#### 1. Adjacency List

Structure

```python
adj = [
    [1, 2],      # neighbors of node 0
    [0, 3],      # neighbors of node 1
    [0],         # neighbors of node 2
    [1]
]
```

Traversal

```python
for nei in adj[node]:
    # nei is the neighbor node
```

---

#### 2. Adjacency Matrix

Structure

```python
matrix = [
    [1,1,0],
    [1,1,1],
    [0,1,1]
]
```

Traversal

```python
for nei in range(n):
    if matrix[node][nei]:
        # nei is the neighbor node
```

---

## Build Undirected Graph

```python
def build_undirected_graph(n, edges):
    adj = [[] for _ in range(n)]

    for u, v in edges:
        adj[u].append(v)
        adj[v].append(u)

    return adj
```

---

## Build Directed Graph

```python
def build_directed_graph(n, edges):
    adj = [[] for _ in range(n)]

    for u, v in edges:
        adj[u].append(v)

    return adj
```

---

## Build Weighted Undirected Graph

```python
def build_weighted_undirected_graph(n, edges):
    adj = [[] for _ in range(n)]

    for u, v, w in edges:
        adj[u].append((v, w))
        adj[v].append((u, w))

    return adj
```

---

## Build Weighted Directed Graph

```python
def build_weighted_directed_graph(n, edges):
    adj = [[] for _ in range(n)]

    for u, v, w in edges:
        adj[u].append((v, w))

    return adj
```

---

## Generic BFS

```python
from collections import deque

def bfs(start, adj):
    n = len(adj)

    visited = [False] * n
    visited[start] = True

    queue = deque([start])

    order = []

    while queue:
        node = queue.popleft()
        order.append(node)

        for nei in adj[node]:
            if not visited[nei]:
                visited[nei] = True
                queue.append(nei)

    return order
```

---

## BFS for All Components

```python
from collections import deque

def bfs_all(adj):
    n = len(adj)

    visited = [False] * n

    components = []

    for start in range(n):

        if visited[start]:
            continue

        queue = deque([start])
        visited[start] = True

        component = []

        while queue:

            node = queue.popleft()
            component.append(node)

            for nei in adj[node]:

                if not visited[nei]:
                    visited[nei] = True
                    queue.append(nei)

        components.append(component)

    return components
```

---

## Generic DFS

```python
def dfs(start, adj):
    n = len(adj)

    visited = [False] * n

    order = []

    def helper(node):
        visited[node] = True
        order.append(node)

        for nei in adj[node]:
            if not visited[nei]:
                helper(nei)

    helper(start)

    return order
```

---

## DFS for All Components

```python
def dfs_all(adj):
    n = len(adj)

    visited = [False] * n

    components = []

    def helper(node):
        visited[node] = True
        component.append(node)

        for nei in adj[node]:
            if not visited[nei]:
                helper(nei)

    for i in range(n):

        if not visited[i]:
            component = []
            helper(i)
            components.append(component)

    return components
```
