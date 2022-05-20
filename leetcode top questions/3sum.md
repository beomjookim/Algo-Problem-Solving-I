## 풀이

간만에 medium 다웠던 문제.  
일반적인 n^3을 시전하니 불통이 떴다. dictionary나 set으로 그 미만으로 줄여보려다가 포기했다.  
그런데 n^3을 시전해도 예외로 skip하는 부분을 넣으면 괜찮더라. 아래의 풀이처럼.  

```python
class Solution:
    def threeSum(self, nums):
        res = []
        nums.sort()
        for i in xrange(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if s < 0:
                    l +=1 
                elif s > 0:
                    r -= 1
                else:
                    res.append((nums[i], nums[l], nums[r]))
                    while l < r and nums[l] == nums[l+1]:
                        l += 1
                    while l < r and nums[r] == nums[r-1]:
                        r -= 1
                    l += 1; r -= 1
        return res
```

이것보다 더 좋은 풀이가 있다. 내가 생각했던 것처럼, n, z, p로 나누어 푸는 것이다... 이후에 iteration을 O(1)에 진행하기 위해 set을 써준 것.  

```python
from collections import defaultdict

class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        neg = defaultdict(int)
        pos = defaultdict(int)
        zeros = 0
        
        for x in nums:
            if x < 0:
                neg[x] += 1
            elif x > 0:
                pos[x] += 1
            else:
                zeros += 1
        
        r = []
        
        if zeros:
            for n in neg:
                if -n in pos:
                    r.append((0, n, -n))
        
            if zeros > 2:
                r.append((0,0,0))

        for set_a, set_b in ((neg, pos), (pos, neg)):
            set_a_items = list(set_a.items())
            for i, (x, q) in enumerate(set_a_items):
                for x2, q2 in set_a_items[i:]:
                    if x != x2 or (x == x2 and q > 1):
                        if -x-x2 in set_b:
                            r.append((x, x2, -x-x2))

        return r
```
