# Binary Tree Postorder Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/930/)  

### Explanation:
TLDR: 

## Solution Recursive:
```Python
class Solution(object):
    def postorderTraversal(self, root):
        
        def inorder(node, answer):
            if not node:
                return answer

            inorder(node.left, answer)
            inorder(node.right, answer)
            answer.append(node.val)
            return answer
            
        return inorder(root, [])
```

## Solution Iterative:
```Python
class Solution(object):
    def peek(self, stack):
        if stack == []:
            return None
        return stack[-1]

    def postorderTraversal(self, root):
        answer = []
        
        stack = []
        current = root
        prev = None
        while stack or current:
            # go as far right as possible adding the current to the travel stack
            if current:
                stack.append(current)
                current = current.left
            # then start going right after moving up the stack (moving up the stack of right nodes)
            else:
                peekNode = self.peek(stack)
                if peekNode.right and prev != peekNode.right:
                    current = peekNode.right
                else:
                    answer.append(peekNode.val)
                    prev = stack.pop()
        
        return answer
```
