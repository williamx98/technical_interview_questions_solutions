# Merge Two Sorted Lists  

[Question Link](https://leetcode.com/problems/merge-two-sorted-lists/)  

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        l1P = l1
        l2P = l2
        
        newHead = ListNode(None)
        pointer = newHead
        
        while l1P or l2P:
            if l1P is None and l2P is not None:
                pointer.next = l2P
                break
            
            if l2P is None and l1P is not None:
                pointer.next = l1P
                break
            
            if l1P is not None and (l2P is None or l1P.val <= l2P.val):
                pointer.next = l1P
                l1P = l1P.next
            else:
                pointer.next = l2P
                l2P = l2P.next    
            
            pointer = pointer.next
        
        return newHead.next
```