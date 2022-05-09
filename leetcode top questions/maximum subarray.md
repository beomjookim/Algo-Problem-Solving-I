## 풀이

앞에서부터 더해가되, 만약 누적이 음수면 reset 한다.

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        res, temp = -float('inf'), 0
        for num in nums:
            temp += num
            if temp > res: res = temp
            if temp < 0: temp = 0
        return res
```
