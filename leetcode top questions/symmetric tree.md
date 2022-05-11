## 풀이

나는 왼쪽과 오른쪽에 포인터를 넣고 좌우 대칭으로 순회를 시켜줬다.  

```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        p1, p2 = root.left, root.right
        a1, a2 = [], []
        
        def trav1(node):
            if node:
                a1.append(node.val)
                trav1(node.right)
                trav1(node.left)
            else: a1.append('king')
        
        def trav2(node):
            if node:
                a2.append(node.val)
                trav2(node.left)
                trav2(node.right)
            else: a2.append('king')
        
        trav1(p1)
        trav2(p2)
        
        return a1 == a2
```

그런데 stack을 활용한 녀석도 있다.

```python
class Solution:
    def isSymmetric(self, root):
        if root is None:
            return True
        stack = [(root.left, root.right)]
        while stack:
            left, right = stack.pop()
            if left is None and right is None:
                continue
            if left is None or right is None:
                return False
            if left.val == right.val:
                stack.append((left.left, right.right))
                stack.append((left.right, right.left))
            else:
                return False
        return True
```
