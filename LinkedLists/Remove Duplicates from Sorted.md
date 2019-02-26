# Remove Duplicates from Sorted   

[Question Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)  

Given a sorted linked list, delete all duplicates such that each element appear only once.  

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
        if head is None:
            return None
        
        pointer = head
        while pointer is not None and pointer.next is not None:
            if pointer.val == pointer.next.val:
                pointer.next = pointer.next.next
            else:
                pointer = pointer.next
        
        return head
```