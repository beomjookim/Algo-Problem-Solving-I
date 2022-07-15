## 풀이

위상정렬에 관한 문제. dfs/ bfs로 풀 수 있는 문제인데, 기존보다 좀 어려웠다.  
dfs가 재귀 형태가 유용하다 보니 꼬리물기 식으로 계속 이어지는 과정을 잘 표현할 수 있다.   
꽤나 생각을 많이 해야 했던 문제.


```python
def canFinish(self, numCourses, prerequisites):
    graph = [[] for _ in xrange(numCourses)]
    visit = [0 for _ in xrange(numCourses)]
    for x, y in prerequisites:
        graph[x].append(y)
    def dfs(i):
        if visit[i] == -1:
            return False
        if visit[i] == 1:
            return True
        visit[i] = -1
        for j in graph[i]:
            if not dfs(j):
                return False
        visit[i] = 1
        return True
    for i in xrange(numCourses):
        if not dfs(i):
            return False
    return True
```
