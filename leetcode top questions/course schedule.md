## 풀이

위상정렬은 degree로 리스트 만들어서 진행해줘야 하는데, 자꾸 까먹는다. 그러나 degree가 꼭 필요한 건 아니다.  
그냥 그래프로 그리고 잘 생각해보면 답 나온다. 그러나 이건 꽤 어려운 문제긴 했다...


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
