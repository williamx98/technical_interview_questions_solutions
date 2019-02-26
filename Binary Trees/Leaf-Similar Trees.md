# Leaf-Similar Trees  

[Question Link](https://leetcode.com/problems/leaf-similar-trees/)  

Consider all the leaves of a binary tree.  From left to right order, the values of those leaves form a leaf value sequence.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        def inOrder(root):
            leaves = []
            current = root
            stack = []
            
            while stack or current:
                if current:
                    stack.append(current)
                    current = current.left
                elif stack:
                    current = stack.pop()
                    if not current.left and not current.right:
                        leaves.append(current.val)
                    current = current.right

            return leaves
    
        return inOrder(root1) == inOrder(root2)
```