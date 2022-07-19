##풀이

dfs. 이게 가능해? 싶은 정도의 시간 복잡도를 가지는데 이게 된단다. 앞으로는, 시간 효윺성 때문에 확신이 없더라도 일단 확실한 답안을 내놓고 정답을 확인하는 버릇을 갖자.  

```python
    def partition(self, s):
        def dfs(s, path, res):
            if not s:
                res.append(path[:])
                return
            for i in range(1, len(s)+1):
                if s[:i] == s[i-1::-1]:
                    path.append(s[:i])
                    dfs(s[i:], path, res)
                    path.pop()        
        res = []
        dfs(s, [], res)
        return res
```
