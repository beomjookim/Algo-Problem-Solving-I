- python code

```python
def solution(arr):
    res = arr[0]
    for i in range(1, len(arr)):
        a, b = res, arr[i]
        while b: a, b = b, a%b
        res *= arr[i] // a
    return res
```
