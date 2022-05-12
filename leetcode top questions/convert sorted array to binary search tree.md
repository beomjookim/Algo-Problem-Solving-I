## 풀이

대략 풀었는데, 역시나 이진탐색의 인덱싱 때문에 지레 겁먹고 포기했다. 그런데 역시나 그냥 기본꼴을 쓰면 되는 상황.  
이진탐색 관련된 풀이가 나오면 기본으로 돌아가자. 기본으로...

```python
class Solution(object):
    def sortedArrayToBST(self, nums):
        def convert(left, right):
            if left > right:
                return None
            mid = (left + right) // 2
            node = TreeNode(nums[mid])
            node.left = convert(left, mid - 1)
            node.right = convert(mid + 1, right)
            return node
        return convert(0, len(nums) - 1)
```
