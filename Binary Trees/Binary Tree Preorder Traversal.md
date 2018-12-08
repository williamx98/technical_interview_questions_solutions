# Binary Tree Preorder Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/928/)  

##### Constraints:

### Explanation:
TLDR: currentNode, left, right

### Notes:


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
        answer = []
        
        lefts = []
        current = root
        while lefts or current:
            # go as far left as possible adding the current to the travel stack
            if current:
                lefts.append(current)
                answer.append(current.val)
                current = current.left
            # then start going right after moving up the lefts (moving up the stack of left nodes)
            else:
                current = lefts.pop()
                current = current.right
        
        return answer
```