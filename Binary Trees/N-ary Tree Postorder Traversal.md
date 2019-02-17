# N-ary Tree Postorder Traversal

[Question Link](https://leetcode.com/problems/n-ary-tree-postorder-traversal/)  

Given an n-ary tree, return the postorder traversal of its nodes' values.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if root is None:
            return []
        
        answer = []
        toVisit = [root]

        while toVisit:
            root = toVisit.pop()
            answer.append(root.val)
            toVisit.extend(root.children)
            
        return answer[::-1]
```