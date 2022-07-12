## 풀이

간만에 tree를 다뤄보니까 어색하다.

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode], min_val = float('-inf'), max_val = float('inf')) -> bool:
        if not root: return True
        if not min_val < root.val < max_val: return False
        return self.isValidBST(root.left, min_val, root.val) and self.isValidBST(root.right, root.val, max_val)
```

1. 파라미터로 임의의 값을 내맘대로 추가해서 던져주는 게 신기했다!
2. 재귀든 뭐든 그 다음 단계로 나아갈 때 그 다음 단계의 val까지 건드리기 보다는 그 전 단계에서 매듭 짓는 게 좋다.
3. LC의 형식 상 추가로 함수를 안 만들고 재귀를 쓰려면 self. 해주면 된다.
