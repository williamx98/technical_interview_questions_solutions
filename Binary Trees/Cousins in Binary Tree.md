# Cousins in Binary Tree  

[Question Link](https://leetcode.com/problems/cousins-in-binary-tree/)  

In a binary tree, the root node is at depth 0, and children of each depth k node are at depth k+1.  

Two nodes of a binary tree are cousins if they have the same depth, but have different parents.  

We are given the root of a binary tree with unique values, and the values x and y of two different nodes in the tree.  

Return true if and only if the nodes corresponding to the values x and y are cousins.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def isCousins(self, root, x, y):
        """
        :type root: TreeNode
        :type x: int
        :type y: int
        :rtype: bool
        """
        def search(node, p, level, depth):
            if x in depth and y in depth:
                return depth[x][0] == depth[y][0] and depth[x][1] != depth[y][1]
            elif node:
                if node.val == x:
                    depth[node.val] = (level, p)
                elif node.val == y:
                    depth[node.val] = (level, p)
                    
                search(node.left, node, level + 1, depth)
                return search(node.right, node, level + 1, depth)
        
        return search(root, None, 0, {})
                
```
