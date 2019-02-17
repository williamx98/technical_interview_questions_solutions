# Construct Binary Tree from Inorder and Postorder Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/942/)    
Similar to: [Construct Binary Tree from Preorder and Inorder Traversal Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/943/)  

Given inorder and postorder traversal of a tree, construct the binary tree.

##### Contraints:
You may assume that duplicates do not exist in the tree.

### Explaination:
TLDR: Use the postorder list to figure out which node is the parent node. Then, find the parent node in the inorder list to figure which nodes are the left subtree and the right subtree.  

The parent node will always be the last node of a postorder traversal.  
The same parent node within the inorder traversal will split the inorder list into the two inorder lists of the left subtree and the right subtree.  
Recursively apply the same logic to both subtrees to create the entire tree

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
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        
        def recurse(inorder, postorder):
            # both lists will always be the same length. Only really need to check 1
            # still checking both for redundancy
            if len(inorder) == 0 and len(postorder) == 0:
                return None 

            newNodeVal = postorder[-1]
            # newNodeVal will be guarunteed to be in the inorder list
            newNodeIn = inorder.index(newNodeVal)

   			# The parent node will always be the last node of a postorder traversal.  
			# The same parent node within the inorder traversal will split the inorder list into the two inorder lists of the left subtree and the right subtree.  
            leftTreeIn = inorder[:newNodeIn]
            leftTreePo = postorder[:newNodeIn]
            
            rightTreeIn = inorder[newNodeIn + 1:]
            rightTreePo = postorder[newNodeIn: -1]
            
            newNode = TreeNode(newNodeVal)
            newNode.left = recurse(leftTreeIn, leftTreePo)
            newNode.right = recurse(rightTreeIn, rightTreePo)
            
            return newNode
    
        return recurse(inorder, postorder)
```
