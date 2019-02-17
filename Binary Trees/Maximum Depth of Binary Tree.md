# Maximum Depth of Binary Tree

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/17/solve-problems-recursively/535/)  

Given a binary tree, find its maximum depth.  

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

##### Constraints:

### Explanation:
TLDR: The maximum is the greater depth of the left subtree compared to the right subtree, added to one because the current node counts as a part of the depth.  

This will be a bottom-up approach, going as far down as possible and evaluating as the stack is cleared.
### Notes:


## Solution (Recursive):
```Python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        def recurse(node):
            if not node:
                return 0
            
            # get the length of the left subtree and the right subtree
            leftSubDepth = 1 + recurse(node.left)
            rightSubDepth = 1 + recurse(node.right)
            
            max = leftSubDepth
            if rightSubDepth > max:
                max = rightSubDepth
                
            return max
        
        return recurse(root)
```

## Solution (Iterative):
```Python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Node
        :rtype: int
        """
        if root is None:
            return 0
        
        level = 0
        toVisit = [root]
        
        while toVisit:
            newVisit = []
            level += 1
            while toVisit:
                visit = toVisit.pop()
                if visit.left:
                    newVisit.append(visit.left)

                if visit.right:
                    newVisit.append(visit.right)
            
            toVisit = newVisit
            
        return level
```