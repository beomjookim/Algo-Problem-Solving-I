## 풀이

걍 주어진 레인지에서 값 찾아내기. 이진탐색이 제일 빠르니까 ㄱㄱ.  
역시 이진탐색은 적용하기가 엿같다. 짜증나는 놈.  
이진탐색은 무조건 기본형에서 벗어나지 않게 한다. 그래야 변형할 수 있다.  

```python
class Solution:
    def mySqrt(self, x):
        lo, hi = 0, x
        
        while lo <= hi:
            mid = (lo + hi) // 2
            
            if mid * mid > x: hi = mid - 1
            elif mid * mid < x: lo = mid + 1
            else: return mid
        return hi
```
