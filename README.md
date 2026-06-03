## Helper Functions

#### Reverse Integers
```python
def reverse(self, n):
  return int(str(n)[::-1])
```

#### Check if number is Power of 2
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n >0 and (n&n-1) == 0
```

#### Check if number is Power of 3
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n > 0 and 1162261467%n == 0
```

#### Check if number is Power of 4
```python
def isPowerOfTwo(self, n: int) -> bool:
  return n > 0 and n & (n-1) == 0 and (n & 0x55555555) != 0
```
