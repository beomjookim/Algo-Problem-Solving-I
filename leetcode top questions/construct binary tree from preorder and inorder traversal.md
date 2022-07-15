## 풀이

tree에 대해 잘 알고 있는지 하는 문제였는데, 꽤 어렵다. 이 정도는 가볍게 풀어야 구글에 갈텐데.  
preorder와 inorder 간에 접점을 찾으려면 unique한 value로 찾을 수 밖에 없지 않을까 했는데, 역시 조건에 있었다.  
다만 어떤 식으로 전개해 나갈지가 의문이었는데, preorder를 앞에서부터 짜르고 inorder를 슬라이싱하는 게 답이었다.  
다시 풀어봐야할 문제.

```python
class Solution:
    def buildTree(self, preorder, inorder):
        if inorder:
            val = preorder.pop(0)
            root = TreeNode(val)
            ind = inorder.index(val)
            root.left = self.buildTree(preorder, inorder[0:ind])
            root.right = self.buildTree(preorder, inorder[ind+1:])
            return root
```
