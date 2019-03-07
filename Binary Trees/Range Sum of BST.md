# Range Sum of BST  

[Question Link](https://leetcode.com/problems/range-sum-of-bst/)  

Given the root node of a binary search tree, return the sum of values of all nodes with value between L and R (inclusive).  

The binary search tree is guaranteed to have unique values.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def rangeSumBST(self, root, L, R):
        def recurse(node):
            if not node:
                return 0
            
            if node.val >= L and node.val <= R:
                return node.val + recurse(node.right) + recurse(node.left)
            elif node.val < L:
                return recurse(node.right)
            elif node.val > R:
                return recurse(node.left)
            
            return currentTotal
        
        return recurse(root)
```

## Solution:
```Python
class Solution(object):
    def rangeSumBST(self, root, L, R):
        ans = 0
        stack = [root]
        while stack:
            node = stack.pop()
            if node:
                if L <= node.val <= R:
                    ans += node.val
                if L < node.val:
                    stack.append(node.left)
                if node.val < R:
                    stack.append(node.right)
        return ans
```