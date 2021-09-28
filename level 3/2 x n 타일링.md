- python code

```python
def solution(n):
    chart = [0, 1, 2, 3, 5]
    if n <= 4: return chart[n]
    chart += [0 for _ in range(n-4)]
    for i in range(5, n+1): chart[i] = (chart[i-1] + chart[i-2]) % 1000000007
    return chart[n]
```
