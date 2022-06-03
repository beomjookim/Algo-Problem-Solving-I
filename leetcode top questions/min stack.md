## 풀이

이게 진짜 머리 좋은 사람을 위한 문제. 어차피 stack은 특성상 꽁무니에서만 출입이 발생한다.  
그러니까 만약 A라는 녀석이 들어오면서 기존의 min 값보다 작아서 min 값이 바뀐다 한들 기존의 멤버들에게는 영향을 미치지 않는다.  
즉, 새로운 값을 넣을 때마다 함께 갱신된 최소값을 넣어준다. 직접 그 최소값을 삭제해야하는 게 아니므로 reference가 아닌 copy 값을 넣는다...  

```python
class MinStack(object):

    def __init__(self):
        self.stack = []
        
    def push(self, x):
        self.stack.append((x, min(self.getMin(), x))) 
           
    def pop(self):
        self.stack.pop()

    def top(self):
        if self.stack:
            return self.stack[-1][0]
        
    def getMin(self):
        if self.stack:
            return self.stack[-1][1]
        return sys.maxint   
```
