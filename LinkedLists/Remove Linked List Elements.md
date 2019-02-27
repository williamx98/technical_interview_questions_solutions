# Remove Linked List Elements  

[Question Link](https://leetcode.com/problems/remove-linked-list-elements/)  

Remove all elements from a linked list of integers that have value val.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        dummyHead = ListNode(None)
        dummyHead.next = head
        prev = dummyHead
        pointer = head
        
        while pointer:
            if pointer.val == val:
                prev.next = pointer.next
                pointer = prev.next
            else:
                prev = pointer
                pointer = pointer.next
            
        return dummyHead.next
```