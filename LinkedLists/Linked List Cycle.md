# Linked List Cycle  

[Question Link](https://leetcode.com/problems/linked-list-cycle/)  

Given a linked list, determine if it has a cycle in it.  

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.  

##### Constraints:

### Explanation:
TLDR: Have a pointer than travels faster than another. If there is a cycle, then the slow pointer will run into the fast pointer at some point.

### Notes:


## Solution:
```Python
class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        if head is None:
            return False
        
        slow = head
        fast = head.next
        
        while fast is not None and fast.next is not None:
            if slow.val == fast.val:
                return True
            
            slow = slow.next
            fast = fast.next.next
                
        return False
```