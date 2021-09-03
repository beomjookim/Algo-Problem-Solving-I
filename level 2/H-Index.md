- python code

```python
def solution(citations):
    answer = 0
    citations.sort(reverse = True)
    for i, c in enumerate(citations): 
        if i+1 <= c: answer = i+1
        else: break
    return answer
```
