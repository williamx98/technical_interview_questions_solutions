# Symmetric Tree

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/17/solve-problems-recursively/536/)  

Given a binary tree, check whether it is a mirror of itself i.e, symmetric around its center). Left subtree = right subtree

##### Constraints:

### Explanation:
TLDR: Go through both trees at the same time checking first for matching children existence. 

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
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root:
            return True
        
        def recursive(leftTreeNode, rightTreeNode):
        	# if both nodes are NULL, then tree is matching to this point
            if not leftTreeNode and not rightTreeNode:
                return True
            
            # if either tree is not NULL, then the tree can not be matching as we already checked if they are both NULL.
            # either both are not NULL or only one is NULL meaning that the tree is no longer the same
            # checking for matching children existence.
            if not leftTreeNode or not rightTreeNode:
                return False
            
            # only thing left to check is their values
            if leftTreeNode.val != rightTreeNode.val:
                return False
            
            # BOTH subtrees have to be matching therefore, use AND operator.
            return recursive(leftTreeNode.left, rightTreeNode.right) and recursive(leftTreeNode.right, rightTreeNode.left)
        
        return recursive(root.left, root.right)
            
```

## Solution Without Comments:
```Python
class Solution(object):
    def isSymmetric(self, root):
        if not root:
            return True
        
        def recursive(leftTreeNode, rightTreeNode):
            if not leftTreeNode and not rightTreeNode:
                return True

            if not leftTreeNode or not rightTreeNode:
                return False
            
            if leftTreeNode.val != rightTreeNode.val:
                return False
            
            return recursive(leftTreeNode.left, rightTreeNode.right) and recursive(leftTreeNode.right, rightTreeNode.left)
        
        return recursive(root.left, root.right)
```