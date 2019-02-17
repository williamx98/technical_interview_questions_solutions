#  N-ary Tree Preorder Traversal

[Question Link](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)  

Given an n-ary tree, return the preorder traversal of its nodes' values.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution (Recursive):
```Python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        def recurse(node, answer):
            if node is None:
                return answer
            
            answer.append(node.val)
            for child in node.children:
                recurse(child, answer)
                
            return answer
        
        return recurse(root, [])     
```

## Solution (Iterative):
```Python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if not root:
            return []
        
        answer = []
        stack = [root]
        
        while stack:
            u = stack.pop()
            answer.append(u.val)
            if u.children:
                for c in u.children[::-1]:
                    stack.append(c)
        return answer
```