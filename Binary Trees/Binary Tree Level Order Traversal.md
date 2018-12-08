# Binary Tree Level Order Traversal

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/931/)  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution With Comments:
```Python
class Solution:
    def levelOrder(self, root):
        answer = []
        def recursive(root, level):
            if root:
                if level < len(answer):
                    answer[level].append(root.val)
                else:
                    answer.append([root.val])
                recursive(root.left, level + 1)
                recursive(root.right, level + 1)
        recursive(root, 0)
        return answer
            
```

## Solution Without Comments:
```Python
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []
        
        answer = []
        toVisit = [root]
        while toVisit:
            sLen = len(toVisit)
            level = []
            for _ in range(sLen):
                node = toVisit[0]
                del toVisit[0]
                level.append(node.val)
                
                if node.left:
                    toVisit.append(node.left)
                if node.right:
                    toVisit.append(node.right)
            answer.append(level)
        
        return answer
```