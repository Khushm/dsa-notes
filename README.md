## Helper Functions

#### Reverse Integers
```python
def reverse(self, n):
  return int(str(n)[::-1])
```

#### Check if Power of 2
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n >0 and (n&n-1) == 0
```

#### Check if Power of 3
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n > 0 and 1162261467%n == 0
```

#### Check if Power of 4
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n > 0 and n & (n-1) == 0 and (n & 0x55555555) != 0
```

#### Check if Prime
```python
def isPrime(self, n: int) -> bool:
  return n > 1 and all(n%i != 0 for i in range(2, int(n**0.5)+1))
```

#### Graph: BFS Traversal (Connected graph)
```python
from collections import deque
def bfs(adj):
  n = len(adj)
  queue = deque([0])
  visited = [False] * n
  visited[0] = True

  ans = []
  
  while queue:
    node = queue.popleft()
    ans.append(node)

    for nei in adj[node]:
      if not visited[nei]:
          visited[nei] = True
          queue.append(nei)
  
  return ans
```

#### Graph: BFS Traversal (Disconnected graph)
```python
from collections import deque

def bfs_all(adj):
  n = len(adj)
  visited = [False] * n
  ans = []

  for start in range(n):
    if visited[start]:
        continue
  
    queue = deque([start])
    visited[start] = True
  
    while queue:
      node = queue.popleft()
      ans.append(node)
  
      for nei in adj[node]:
        if not visited[nei]:
            visited[nei] = True
            queue.append(nei)
  
  return ans
```

#### Graph: Generic BFS Traversal (for any start node)
```python
from collections import deque
def bfs(start, adj):
  n = len(adj)
  queue = deque([start])
  visited = [False] * n
  visited[start] = True

  ans = []
  
  while queue:
    node = queue.popleft()
    ans.append(node)
    for nei in adj[node]:
        if not visited[nei]:
            visited[nei] = True
            queue.append(nei)

  return ans
```
