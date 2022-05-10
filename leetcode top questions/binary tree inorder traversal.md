## 풀이

나도 쉽게 풀었지만, one-liner가 있어서 깜놀.

### 내 풀이
```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        def inorder(temp):
            if temp.left: inorder(temp.left)
            res.append(temp.val)
            if temp.right: inorder(temp.right)
        res = []
        if root: inorder(root)
        return res
```

### one liner
```python
class Solution:
    def inorder(root):
      return  inorder(root.left) + [root.val] + inorder(root.right) if root else []
```
