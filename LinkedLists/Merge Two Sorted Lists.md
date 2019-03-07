# Merge Two Sorted Lists  

[Question Link](https://leetcode.com/problems/merge-two-sorted-lists/)  

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.  

##### Constraints:

### Explanation:
TLDR: Set the point to the next node, move up that list's pointer, move the answer pointer to its new node. Optimze by quiting when EITHER list reach their end. Before returning the answer, attach the remining list's unchecked and attach to the end of the answer list.  

### Notes:


## Solution:
```Python
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        l1P = l1
        l2P = l2
        
        newHead = ListNode(None)
        pointer = newHead
        
        while l1P and l2P:            
            if l1P.val <= l2P.val:
                pointer.next = l1P
                l1P = l1P.next
            else:
                pointer.next = l2P
                l2P = l2P.next  
            
            pointer = pointer.next
            
        if l1P:
            pointer.next = l1P
        elif l2P:
            pointer.next = l2P
        
        return newHead.next
```