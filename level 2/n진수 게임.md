- python code

```python
def solution(n, t, m, p):
    res, curNum, curTurn = '', 0, 0
    p -= 1
    
    def convert(num):
        dic = {10:'A', 11:'B', 12:'C', 13:'D', 14:'E', 15:'F'}
        conv = ''
        while num:
            conv += str(num%n) if num%n < 10 else dic[num%n]
            num //= n
        return conv[::-1] if conv != '' else '0'
    
    while True:
        for c in convert(curNum):
            if curTurn%m == p: res += c
            if len(res) == t: return res
            curTurn += 1
        curNum += 1
```
