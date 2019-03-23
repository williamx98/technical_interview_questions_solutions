# Add Two Numbers II  

[Question Link](https://leetcode.com/problems/add-two-numbers-ii/)  

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.  

You may assume the two numbers do not contain any leading zero, except the number 0 itself.  

### Explanation:
TLDR:  Reverse the two lists. Then assemble the answer list by moving down the two reversed lists at the same time.

## Solution:
```Python
class Solution:
    def addTwoNumbers(self, l1, l2):
        def reverse(head):
            if head is None or head.next is None:
                return head
        
            newHead = None
            current = head
            while current:
                oldNext = current.next
                current.next = newHead
                newHead = current
                current = oldNext
            
            return newHead
        
        l1 = reverse(l1)
        l2 = reverse(l2)
        
        currentHead = None
        rem = 0
        while l1 or l2 or rem:
            total = rem
            
            if l1:
                total += l1.val
                l1 = l1.next
                
            if l2:
                total += l2.val
                l2 = l2.next
            
            rem = total // 10
            toAdd = ListNode(total % 10)
            toAdd.next = currentHead
            currentHead = toAdd
            
        return currentHead
```
