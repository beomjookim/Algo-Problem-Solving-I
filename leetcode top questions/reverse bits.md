## 풀이

bit manipulation. reverse는 안 먹힌다.  
bin 등은 내가 그 값을 이진수로 확인하고자 쓰는 함수지, shift나 bit manipulation 시에 이진수로 굳이 바꾸지 않아도 문제없다.

```python
class Solution:
    def reverseBits(self, n):
        ans = 0
        for i in range(32):
            ans = (ans << 1) + (n & 1)
            n >>= 1
        return ans
```
