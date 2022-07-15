## 풀이

위상정렬에 관한 문제. dfs/ bfs로 풀 수 있는 문제인데, 기존보다 좀 어려웠다.  
dfs가 재귀 형태가 유용하다 보니 꼬리물기 식으로 계속 이어지는 과정을 잘 표현할 수 있다.   
꽤나 생각을 많이 해야 했던 문제.


```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        dic = {i:set() for i in range(numCourses)}
        for b, a in prerequisites: dic[b].add(a)
        
        for j in range(numCourses): 
            visitSet = set()
            
            def dfs(crs):
                if crs in visitSet: return False            
                visitSet.add(crs)
                for pre in dic[crs]:
                    if not dfs(pre): return False
                dic[crs] = set()
                visitSet.remove(crs)
            
                return True
            
            if not dfs(j): return False
        return True
```
