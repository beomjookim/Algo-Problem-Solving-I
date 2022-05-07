## 나의 풀이

전형적인 문제. stack으로 O(N) 풀이.

```python
s = "()[]{}("
stack = []

for c in s:
    if c in [")", "}", "]"]:
        if (c == ")" and stack[-1] == "(") or (c == "}" and stack[-1] == "{") or (c == "]" and stack[-1] == "["): stack.pop()
        else: return False
    else: stack.append(c)

return not stack
```
