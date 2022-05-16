## 풀이

bit manipulation. reverse는 안 먹힌다.  

```python
class Solution:
    def reverseBits(self, n):
        ans = 0
        for i in range(32):
            ans = (ans << 1) + (n & 1)
            n >>= 1
        return ans
```
