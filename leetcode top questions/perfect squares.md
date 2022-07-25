## 풀이

재귀라는 건 알지만 어찌 풀어나갈지 애매하다.  
삼성에서도 이런 문제가 많이 나오는 것 같으니, 풀이 방법을 확실히 해두자.  

와... 당연히 재귀로 풀어야 할 거라고 생각했는데, https://leetcode.com/problems/perfect-squares/discuss/71475/Short-Python-solution-using-BFS  
어쩌면 최단거리이므로 BFS로 손쉽게 풀 수 있었다. 꼭 2D 상의 최단거리가 아니더라도 최단거리로 파악할 수 있어야 하겠다.  


```python
def numSquares(self, n):
    if n < 2:
        return n
    lst = []
    i = 1
    while i * i <= n:
        lst.append( i * i )
        i += 1
    cnt = 0
    toCheck = {n}
    while toCheck:
        cnt += 1
        temp = set()
        for x in toCheck:
            for y in lst:
                if x == y:
                    return cnt
                if x < y:
                    break
                temp.add(x-y)
        toCheck = temp

    return cnt
```
