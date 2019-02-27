# Rotate List  

[Question Link](https://leetcode.com/problems/rotate-list/)  

Given a linked list, rotate the list to the right by k places, where k is non-negative.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        if head is None or head.next is None:
            return head
        
        # find the length of the list
        length = 1
        current = head
        while current.next:
            length += 1
            current = current.next
        
        # find how many spots to shift over
        k = k % length
        if k == 0:
            return head
        
        # turn list into cycle. attach end to front
        current.next = head
        
        # shift up to that position
        length = length - k
        current = head    
        while length > 1:
            length = length - 1
            current = current.next
        
        # split the list
        newHead = current.next
        # make sure to set the other end's next to null, otherwise, it'd still be a cycle
        current.next = None
        
        return newHead
```