# Remove Duplicates from Sorted List II  

[Question Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)  

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head is None or head.next is None:
            return head
        
        dummy = ListNode(None)
        dummy.next = head

        prev = dummy
        next = head
        
        while next:
            while next.next and next.val == next.next.val:
                next = next.next
                
            if prev.next == next:
                prev = next
            else:
                prev.next = next.next
                
            next = next.next
        
        return dummy.next
```