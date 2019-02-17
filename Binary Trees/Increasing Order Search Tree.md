# Increasing Order Search Tree  

[Question Link](https://leetcode.com/problems/increasing-order-search-tree/)  

Given a tree, rearrange the tree in in-order so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only 1 right child.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def increasingBST(self, root):
    	def recurse(node, tail):
    		# if null node is left child, tail is its parent
    		# if null node is right child, tail is its parent parent
    		if node is None:
    			return tail

    		# go left, pass parent
    		res = recurse(node.left, node)

    		# set node left None to mimick linkedlist
    		node.left = None

    		# set node right to be tail (parent when left chld)
    		# (parent parent when right chld)
    		node.right = recurse(node.right, tail)

    		# left most path of the original tree
    		return res

    	return recurse(root, None)
```

## Solution:
```Python
class Solution(object):
    def increasingBST(self, root):
        current = root
        stack = []
        head = TreeNode(0)
        prev = head
        while stack or current:
            if current:
                stack.append(current)
                current = current.left
            else:
                visit = stack.pop()
                prev.right = visit
                visit.left = None
                prev = visit
                current = visit.right
                
        return head.right
```