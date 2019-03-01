# Construct Binary Tree from Preorder and Inorder Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/943/)     
Similar to: [Construct Binary Tree from Inorder and Postorder Traversal Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/942/)  

Given preorder and inorder traversal of a tree, construct the binary tree.

##### Constraints:
You may assume that duplicates do not exist in the tree.

### Explanation:
TLDR: Use the preorder list to figure out which node is the parent node. Then, find the parent node in the inorder list to figure which nodes are the left subtree and the right subtree.  

The parent node will always be the first node of a preorder traversal.  
The same parent node within the inorder traversal will split the inorder list into the two inorder lists of the left subtree and the right subtree.  
Recursively apply the same logic to both subtrees to create the entire tree

## Solution:
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: TreeNode
        """
        
        def recurse(preorder, inorder):
            # both lists will always be the same length. Only really need to check either list
            # still checking both for redundancy
            if len(preorder) == 0 or len(inorder) == 0:
                return None
            
            newNodeVal = preorder[0]
            # newNodeVal will be guarunteed to be in the inorder list
            newNodeIn = inorder.index(newNodeVal)
        	
   			# The parent node will always be the first node of a preorder traversal.  
			# The same parent node within the inorder traversal will split the inorder list into the two inorder lists of the left subtree and the right subtree.  
            leftTreeIn = inorder[:newNodeIn]
            leftTreePo = preorder[1:newNodeIn + 1]
            
            rightTreeIn = inorder[newNodeIn + 1:]
            rightTreePo = preorder[newNodeIn + 1:]
            
            newNode = TreeNode(newNodeVal)
            newNode.left = recurse(leftTreePo, leftTreeIn)
            newNode.right = recurse(rightTreePo, rightTreeIn)
            return newNode
        
        return recurse(preorder, inorder)
```
