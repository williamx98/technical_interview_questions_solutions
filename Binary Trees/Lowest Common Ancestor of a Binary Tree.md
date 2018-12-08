# Lowest Common Ancestor of a Binary Tree

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/932/)  

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

##### Constraints:

### Explanation:
TLDR: return root when end of tree or EITHER p or q has been found

When p is ancestor of q, q will never be "found" because its not necessary since p is the answer. Vice versa is true.  
When p and q are in different trees, one ancestor node will eventually have both left and right 

### Notes:


## Solution Recursive:
```Python
class Solution(object):
    def lowestCommonAncestor(self, root, p, q):
        if root is None or root is p or root is q: 
            return root
        
        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)
        
        if left and right:
            return root
        elif left:
        	return left
        elif right:
        	return right
```

## Solution Iterative:
```Python
class Solution(objectect):
	def lowestCommonAncestor(self, root, p, q):
	    stack = [root]
	    parent = {root: None}
	    while (p in parent and q in parent) == False:
	        node = stack.pop()
	        if node.left:
	            parent[node.left] = node
	            stack.append(node.left)
	        if node.right:
	            parent[node.right] = node
	            stack.append(node.right)

	    ancestors = set()
	    # create path from p to root
	    while p:
	        ancestors.add(p)
	        p = parent[p]

	    # while q is not in the path from p to root, travel back on path from q to root.
	    while q not in ancestors:
	        q = parent[q]

	    return q
```