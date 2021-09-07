- python code

```python
def solution(s): return ' '.join([word[0].upper() + word[1:].lower() if word else '' for word in s.split(' ')])
```
