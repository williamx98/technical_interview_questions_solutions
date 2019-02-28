# Delete Node in a Linked List  
### Rating: [3/5] Simple problem but easy to be tripped up if never seen before.

[Question Link](https://leetcode.com/problems/delete-node-in-a-linked-list/)  

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def deleteNode(self, node):
        node.val = node.next.val
        node.next = node.next.next
```
