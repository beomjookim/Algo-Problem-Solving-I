## 풀이

재귀라는 건 알지만 어찌 풀어나갈지 애매하다.  
삼성에서도 이런 문제가 많이 나오는 것 같으니, 풀이 방법을 확실히 해두자.  

와... 당연히 재귀로 풀어야 할 거라고 생각했는데, https://leetcode.com/problems/perfect-squares/discuss/71475/Short-Python-solution-using-BFS  
어쩌면 최단거리이므로 BFS로 손쉽게 풀 수 있었다. 꼭 2D 상의 최단거리가 아니더라도 최단거리로 파악할 수 있어야 하겠다.  


```python
from math import ceil

class Solution:
    def numSquares(self, n: int) -> int:
        cand = set({n})
        squares = [i**2 for i in range(1, ceil((n+1)**.5))]
        res = 0
        
        while True:
            res += 1
            temp = set()
                        
            for val in cand:
                if val in squares: return res
                
                for sq in squares:
                    if val < sq: break
                    temp.add(val-sq)
                        
            cand = temp
```

받은 힌트를 토대로 내 방식대로 다시 풀어보았다. 최단거리 문제라는 걸 알고 나면 훨씬 수월해짐.
