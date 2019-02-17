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
        answer = []
        def recursive(root, level, answer):
            if root is None:
                return answer

            if level < len(answer):
                answer[level].append(root.val)
            else:
                answer.append([root.val])
            recursive(root.left, level + 1)
            recursive(root.right, level + 1)

            return answer

        return recursive(root, 0, [])
```


## Iterative:
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

## Variant (No Per-Level Separation):
```Python
class Solution:
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
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

# Variant (Per-Level Separation):
```Python
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        
        queue = [[root]]
        
        index = 0
        level = 0
        
        while level < len(queue):            
            current = queue[level][index]
            
            if (current.left or current.right) and level >= len(queue) - 1:
                queue.append([])
            
            if current.left:
                queue[level + 1].append(current.left)
            
            if current.right:
                queue[level + 1].append(current.right)
                
            index += 1
            if index >= len(queue[level]):
                index = 0
                level = level + 1

        answer = []
        for row in queue:
            answer.append([])
            for item in row:
                answer[-1].append(item.val)
        
        return answer
```

# Variant (Per-Level Separation):
```Python
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        
        queue = [root, None]
        index = 0
        while index < len(queue):
            current = queue[index]
            index = index + 1
            
            if current is None:
                if queue[-1] is not None:
                    queue.append(None)
                continue;

            if current.left:
                queue.append(current.left)
            
            if current.right:
                queue.append(current.right)
        
        answer = [[]]
        answerLevel = 0
        for item in queue[0:len(queue) - 1]:
            if item == None:
                answer.append([])
                answerLevel = answerLevel + 1
            else:
                answer[answerLevel].append(item.val)
                
        
        return answer
```