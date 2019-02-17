# Univalued Binary Tree

[Question Link](https://leetcode.com/problems/univalued-binary-tree/)  

A binary tree is univalued if every node in the tree has the same value.  

Return true if and only if the given tree is univalued.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
    checkVal = root.val
    toVisit = [root]
    while toVisit:
        node = toVisit.pop()
        if node.val != checkVal:
            return False
        else:
            if node.left != None:
                toVisit.append(node.left)
            if node.right != None:
                toVisit.append(node.right)
    return True
```