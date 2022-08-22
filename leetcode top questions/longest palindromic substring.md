## 풀이

간만에 괜찮은 문제. 각각의 스팟에서 퍼져나가는 방식. odd와 even 케이스를 나누는 게 주효.  

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ''
        
        def isPalindromic(substr): return substr == substr[::-1]
        
        for i in range(len(s)): # 홀수짜리 substring 색출하기
            for j in range(i+1):
                if i+1 + j > len(s): break
                temp = s[i-j:i+j+1]
                if isPalindromic(temp):
                    if len(res) < 2*j+1: res = temp
                else: break
                    
        for k in range(len(s)-1): # 짝수짜리 substring 색출하기
            for l in range(k+1):
                if k+2 + l > len(s): break
                temp = s[k-l:k+2+l]
                if isPalindromic(temp):
                    if len(res) < 2*l+2: res = temp
                else: break                    
        
        return res
```

같은 발상이지만 odd와 even을 통합하고, while을 씀으로써 slicing이 아닌 인덱스를 +-하는 방식도 있다. 이게 더 효율적임.  
그러나 인덱싱이 워낙 예민한 부분이기에 실전에서 이를 바로 생각할 수 있을지는 의문이다.  
이런 발상으로 단 한번의 신택스 에러 없이 풀었다는 것이 나름 고무적이라고 할 수 있음.  
