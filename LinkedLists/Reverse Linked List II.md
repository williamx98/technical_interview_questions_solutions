# Reverse Linked List II  

[Question Link](https://leetcode.com/problems/reverse-linked-list-ii/)  

Reverse a linked list from position m to n. Do it in one-pass.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def reverseBetween(self, head, m, n):
        """
        :type head: ListNode
        :type m: int
        :type n: int
        :rtype: ListNode
        """
        if m == n:
            return head
        
        dummyHead = ListNode(None)
        dummyHead.next = head
        pointer = head
        pre = dummyHead
        
        counter = 1
        while counter < m:
            counter += 1
            pre = pointer
            pointer = pointer.next
            
        newHead = None
        current = pointer
        while current and counter <= n:
            counter += 1
            oldNext = current.next
            current.next = newHead
            newHead = current
            current = oldNext
    
            
        pre.next = newHead
        pointer.next = current
        
        return dummyHead.next
```