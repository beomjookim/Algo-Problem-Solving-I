## 풀이

O(n^2)보다 더 간결한 풀이가 필요. 이 경우 투 포인터로 O(n)으로 커버 가능.  
iteration을 가장 작은 것과 큰 것의 조합부터 시작하므로써 시간이 갈수록 가로는 줄어든다는 성질을 활용.  
l이든 r이든 매번 움직이기는 해야하는데, 뭘 움직일지 생각할 때에 그 다음 녀석이 큰지 작은지는 중요하지 않고, 지금 있는 l과 r 중 더 작은 놈을 움직인다는 전개가 중요.  

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
