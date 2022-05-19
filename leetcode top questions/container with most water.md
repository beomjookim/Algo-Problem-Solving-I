## 풀이

O(n^2)보다 더 간결한 풀이가 필요. 이 경우 투 포인터로 O(n)으로 커버 가능.  
iteration을 가장 작은 것과 큰 것의 조합부터 시작하므로써 시간이 갈수록 가로는 줄어든다는 성질을 활용.  

```python
class Solution:
    def maxArea(self, height):
        L, R, width, res = 0, len(height) - 1, len(height) - 1, 0
        for w in range(width, 0, -1):
            if height[L] < height[R]:
                res, L = max(res, height[L] * w), L + 1
            else:
                res, R = max(res, height[R] * w), R - 1
        return res
```
