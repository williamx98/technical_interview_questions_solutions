# 

[Question Link]()  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution Recursive:
```Python
class Solution(object):
    def postorderTraversal(self, root):
    	answer = []
        
        def inorder(node, answer):
            if not node:
                return

            inorder(node.left, answer)
            inorder(node.right, answer)
            answer.append(node.val)
        
        inorder(root, answer)
        return answer
```

## Solution Iterative:
```Python
class Solution(object):
    def postorderTraversal(self, root):
        answer = []
        
        rights = []
        current = root
        while rights or current:
            # go as far right as possible adding the current to the travel stack
            if current:
                rights.append(current)
                answer.insert(0, current.val)
                current = current.right
            # then start going right after moving up the rights (moving up the stack of right nodes)
            else:
                current = rights.pop()
                current = current.left
        
        return answer
```