# Remove Nth Node From End of List  

[Question Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  

Given a linked list, remove the n-th node from the end of list and return its head.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        dummyHead = ListNode(None)
        dummyHead.next = head
        
        prev = dummyHead
        pointer = head
        
        end = head
        while n > 0:
            n -= 1
            end = end.next
        
        while end:
            end = end.next
            prev = pointer
            pointer = pointer.next
            
        prev.next = pointer.next
        
        return dummyHead.next
```