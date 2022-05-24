## 풀이

node를 리무브하는 건, 실제로 꼭 그걸 리무브할 필요는 없다 아래와 같이.  

```python
class Solution:
    def removeNthFromEnd(self, head, n):
        def index(node):
            if not node:
                return 0
            i = index(node.next) + 1
            if i > n:
                node.next.val = node.val
            return i
        index(head)
        return head.next
```

실제로 리무브 해도 되긴 한다. 아무래도 이게 더 빠르다.  

```python
class Solution:
    def removeNthFromEnd(self, head, n):
        fast = slow = head
        for _ in range(n):
            fast = fast.next
        if not fast:
            return head.next
        while fast.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return head
```
