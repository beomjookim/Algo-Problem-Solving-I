## 풀이

while을 써서 풀었지만, for을 쓰는 게 쓸데없는 예외를 안 만들기 때문에 이게 나은 것 같다.

### 기존 풀이

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        res = [[1]]
        if numRows == 1: return res
        
        while len(res) < numRows:
            temp = res[-1]
            res.append([1] + [temp[i]+temp[i+1] for i in range(len(temp)-1)] + [1])
        
        return res
```

### 더 나은 풀이

```python
class Solution:
    def generate(numRows):
        pascal = [[1]*(i+1) for i in range(numRows)]
        for i in range(numRows):
            for j in range(1,i):
                pascal[i][j] = pascal[i-1][j-1] + pascal[i-1][j]
        return pascal
```
