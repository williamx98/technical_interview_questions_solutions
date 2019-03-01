# Binary Tree Preorder Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/928/)  

### Explanation:
TLDR: currentNode, left, right

## Solution Recursive:
```Python
class Solution(object):
    def preorderTraversal(self, root):
        answer = []
        
        def preorder(node, answer):
            if not node:
                return
            
            answer.append(node.val)
            preorder(node.left, answer)
            preorder(node.right, answer)
        
        preorder(root, answer)
        return answer    
```

## Solution Iterative:
```Python
class Solution(object):
    def preorderTraversal(self, root):
        if root is None:
            return []
        
        answer = []
        stack = [root]
        while stack:
            current = stack.pop()
            answer.append(current.val)

            if current.right:
                stack.append(current.right)

            if current.left:
                stack.append(current.left)
        
        return answer
```
