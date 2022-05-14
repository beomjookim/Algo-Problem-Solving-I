## 풀이

어렵다, 어려워...  
머리를 잘 굴려야만 하는 그런 문제.  

```python
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        ans, pos = 0, 0
        for letter in reversed(columnTitle):
            digit = ord(letter)-64
            ans += digit * 26**pos
            pos += 1
            
        return ans
```
