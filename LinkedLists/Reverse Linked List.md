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

        first = None
        second = head
        
        while second is not None:
            third = second.next
            second.next = first
            first = second
            second = third
        
        return first
```