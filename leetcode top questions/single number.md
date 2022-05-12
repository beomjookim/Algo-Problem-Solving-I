## 풀이

정말 쉬운 문제지만, 내 풀이보다 더 좋은 풀이가 두 개나 있었다. 나는 sorting을 써서 O(nlongn)인데,  

1. python의 set, dictionary의 in은 O(1)이라는 거!!!
2. XOR이라는 대형 기술을 몰랐다. A XOR A = 0 이라는 성질을 이용하면 그만...  

### 기존 풀이
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        nums.sort()
        while nums:
            if len(nums) == 1 or nums[0] != nums[1]: return nums[0]
            else: nums = nums[2:]
```

### 더 나은 풀이
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        xor = 0
        for num in nums:
            xor ^= num
        
        return xor
```
