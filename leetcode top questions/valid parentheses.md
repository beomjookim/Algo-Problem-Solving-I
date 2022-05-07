## 나의 풀이

전형적인 문제. stack으로 O(N) 풀이.

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        pairs = {")": "(", "}": "{", "]": "["}

        for c in s:
            if c in [")", "}", "]"] and stack:
                if pairs[c] == stack[-1]: stack.pop()
                else: return False
            else: stack.append(c)

        return not stack
```
