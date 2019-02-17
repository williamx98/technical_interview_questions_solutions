# Path Sum

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/17/solve-problems-recursively/537/)  

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

##### Constraints:

### Explanation:
TLDR: Conditional tree traversal.  

If the current node is a leaf, then return whether current node value minus the current path's total is equal to 0.
If its not a leaf, try to find a possible path using the left subtree and then the right subtree.
### Notes:


## Solution:
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
        
        def recurse(currentNode, total): 
        	# it is possible that parent node to the current node only has one child but we will end up checking both anyway
        	# immediate invalidate the path that leads to this node since it's not a leaf
            if not currentNode:
                return False
            
            # node is child, check if sum found
            if not currentNode.left and not currentNode.right:
                return total - currentNode.val == 0
            
            # node is not child. temporarily subtract the currentNode value from the left and then the right child nodes 
            # and send them to the next recurse
            return recurse(currentNode.left, total - currentNode.val) or recurse(currentNode.right, total - currentNode.val)
        
        return recurse(root, sum)
```