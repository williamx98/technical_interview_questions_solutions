# Maximum Depth of N-ary Tree

[Question Link](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)  

Given a n-ary tree, find its maximum depth.  

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
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
                if visit.children:
                    newVisit.extend(visit.children)
            
            toVisit = newVisit
            
        return level
```