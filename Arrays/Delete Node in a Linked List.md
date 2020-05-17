# Delete Node in a Linked List  
### Rating: [5/5] Simple problem but easy to be tripped up if never seen before.

[Question Link](https://leetcode.com/problems/delete-node-in-a-linked-list/)  

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.  

### Explanation:
TLDR: What most people know of deleting a node is to connect the previous node to the next node. In this problem, there is no access to the previous node so it's easy to be thrown off by that fact.

## Solution:
```Python
class Solution(object):
    def deleteNode(self, node):
        node.val = node.next.val
        node.next = node.next.next
```
