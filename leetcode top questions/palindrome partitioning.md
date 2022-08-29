##풀이

dfs. 이게 가능해? 싶은 정도의 시간 복잡도를 가지는데 이게 된단다. 앞으로는, 시간 효율성 때문에 확신이 없더라도 일단 확실한 답안을 내놓고 정답을 확인하는 버릇을 갖자.  
인풋과 아웃풋을 고려할 때, 아웃풋을 리턴값으로 가지게 되면 dfs에서는 상당히 비효율적이고 찾기 어려울 수 있다. 그냥 path 뿐만 아니라 res까지도 아규먼트로 넘겨버리자.  
이러면 글로벌 변수를 쓰지 않고도 계속 consistency를 유지할 수 있다. 물론 res의 순서는 뒤죽박죽이 되겠지만, 이번 문제에서 순서는 상관이 없기에.  

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
