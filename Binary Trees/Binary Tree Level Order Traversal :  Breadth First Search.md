# Binary Tree Level Order Traversal / Breadth First Search

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/931/)  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Recursive:
```Python
class Solution:
    def levelOrder(self, root):
        if root is None:
            return []
        
        def recursive(root, level, answer):
            if root is None:
                return
            
            if level < len(answer):
                answer[level].append(root.val)
            else:
                answer.append([root.val])
            recursive(root.left, level + 1, answer)
            recursive(root.right, level + 1, answer)

            return answer

        return recursive(root, 0, [])
```


## Iterative (Per-Level Separation):
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

## Iterative (Per-Level Separation):
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
            newVisit = []
            newLevel = []
            while toVisit:
                visit = toVisit[0]
                del toVisit[0]
                newLevel.append(visit.val)
                
                if visit.left:
                    newVisit.append(visit.left)
                
                if visit.right:
                    newVisit.append(visit.right)
                
            toVisit = newVisit
            answer.append(newLevel)
            
        return answer
```

## Iterative (No Per-Level Separation):
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
            node = toVisit[0]
            del toVisit[0]
            answer.append(node.val)
                
            if node.left:
                toVisit.append(node.left)
            if node.right:
                toVisit.append(node.right)

        return answer
```