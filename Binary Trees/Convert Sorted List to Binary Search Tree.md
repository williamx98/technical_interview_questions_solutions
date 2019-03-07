# Convert Sorted List to Binary Search Tree  

[Question Link](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)  

Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution:
    def sortedListToBST(self, head):
        def count(node):
            size = 0
            while node:
                size += 1
                node = node.next
            return size
        
        def makeTree(size, list):
            if size == 0:
                return None
            
            node = TreeNode(0)
            leftSize = size//2
            node.left = makeTree(leftSize, list)
            node.val = list[0].val
            list[0] = list[0].next
            rightSize = size - leftSize - 1
            node.right = makeTree(rightSize, list)
            return node
            
        return makeTree(count(head), [head])
```