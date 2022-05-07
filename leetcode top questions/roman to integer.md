## 나의 풀이

분기를 더 나누면 좀 더 나을랑가? 별로 의미없을 것 같아 아래처럼 진행함.  

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        dic = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000, 'IV': 4, 'IX': 9, 'XL': 40, 'XC': 90, 'CD': 400, 'CM': 900}
        i = res = 0
        
        while i < len(s):
            if s[i] in ['I', 'X', 'C']:
                if s[i:i+2] in dic:
                    res += dic[s[i:i+2]]
                    i += 2
                    continue
            res += dic[s[i]]
            i += 1
            
        return res
```

그런데, 두 자릿수 짜리를 분기로 다시 한 번 확인할 게 아니라 그냥 그걸 한 자릿수 짜리로 replace 하면 된다! 이게 더 빠르다니!! 놀랍다...  

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        translations = {"I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000, 'E': 4, 'F': 9, 'G': 40, 'H': 90, 'J': 400, 'K': 900}
        s = s.replace("IV", "E").replace("IX", "F").replace("XL", "G").replace("XC", "H").replace("CD", "J").replace("CM", "K")
        return sum([translations[char] for char in s])
```
