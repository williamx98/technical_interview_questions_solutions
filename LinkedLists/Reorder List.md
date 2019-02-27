# Reorder List  

[Question Link](https://leetcode.com/problems/reorder-list/)  

Given a singly linked list L: L0→L1→…→Ln-1→Ln,  
reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→… 

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
class Solution(object):
    def reorderList(self, head):
        """
        :type head: ListNode
        :rtype: void Do not return anything, modify head in-place instead.
        """
        if head is None or head.next is None:
            return
        
        #find the mid point
        midPointer = head;
        doubleSpeed = head;
        midPointerPrev = None;
        while doubleSpeed and doubleSpeed.next:
            midPointerPrev = midPointer;
            midPointer = midPointer.next;
            doubleSpeed = doubleSpeed.next.next;
        midPointerPrev.next = None;
        
        # reverse the second half
        newHead = None
        current = midPointer
        while current:
            oldNext = current.next
            current.next = newHead
            newHead = current
            current = oldNext
        
        # merge
        firstHalf = head
        secondHalf = newHead
        while secondHalf:
            next = firstHalf.next
            firstHalf.next = secondHalf
            firstHalf = secondHalf
            secondHalf = next
        
```