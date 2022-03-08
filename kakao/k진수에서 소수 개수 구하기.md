## 나의 풀이

더할 나위 없는 풀이 ㅋ

```python
from math import floor

def isPrime(s):
    if s == '1': return False
    
    cs = int(s)
    for i in range(2, floor(cs**.5)+1):
        if not cs%i: return False
    return True

def solution(n, k):
    conv = ''
    while n:
        conv += str(n%k)
        n //= k
    
    return sum([isPrime(s) for s in conv[::-1].split('0') if s])
```
