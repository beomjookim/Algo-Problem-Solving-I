## 풀이

좋은 풀이. LL은 이런 풀이가 많다.  
A와 B가 서로 길이가 같다면 당연히 만나고, 서로 길이가 다르다면 서로 switch를 하면서 접점이 있다면 결국 2회차에 만나게 된다.  
없다면 둘 다 None이 될테니까 이를 탈출조건으로 만들면 된다.

```python
class Solution:
    def getIntersectionNode(self, headA, headB):
        if headA and headB:
            A, B = headA, headB
            while A!=B:
                A = A.next if A else headB
                B = B.next if B else headA
            return A
```
