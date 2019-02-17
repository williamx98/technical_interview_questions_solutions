# Merge Two Binary Trees

[Question Link](https://leetcode.com/problems/merge-two-binary-trees/)  
Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.  

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.  


##### Constraints:

### Explanation:
TLDR: Return the new node on each recurse.

### Notes:


## Solution:
```Python
class Solution(object):
    def mergeTrees(self, t1, t2):
        """
        :type t1: TreeNode
        :type t2: TreeNode
        :rtype: TreeNode
        """
        
        def traverse(node1, node2):
            if node1 is None and node2 is None:
                return None
            
            if node1 is None:
                return node2
            
            if node2 is None:
                return node1
            
            node1.val = node1.val + node2.val
            node1.left = traverse(node1.left, node2.left)
            node1.right = traverse(node1.right, node2.right)
            
            return node1
        
        return traverse(t1, t2)
```