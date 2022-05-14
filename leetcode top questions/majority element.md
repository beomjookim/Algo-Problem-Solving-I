## 풀이

O(1) space, O(n) time을 만족시키는 방법... ㄷㄷ  

```python
class Solution:
    def majorityElement(self, nums):
        candidate, count = nums[0], 0
        for num in nums:
            if num == candidate:
                count += 1
            elif count == 0:
                candidate, count = num, 1
            else:
                count -= 1
        return candidate
```
