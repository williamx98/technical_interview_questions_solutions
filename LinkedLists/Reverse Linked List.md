# Reverse Linked List  

[Question Link](https://leetcode.com/problems/reverse-linked-list/)  

Reverse a singly linked list.

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """

        newHead = None
        current = head
        
        while current is not None:
            oldNext = current.next
            current.next = newHead
            newHead = current
            current = oldNext
        
        return newHead
```