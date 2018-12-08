# Path Sum

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/17/solve-problems-recursively/537/)  

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

##### Contraints:

### Explaination:
TLDR: Conditional tree traversal.  

### Notes:


## Solution With Comments:
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if not root:
            return False
        
        def recurse(root, total): 
            if not root:
                return False
            
            if not root.left and not root.right:
                return total - root.val == 0
            
            return recurse(root.left, total - root.val) or recurse(root.right, total - root.val)
        
        return recurse(root, sum)
```

## Solution Without Comments:
```Python

```