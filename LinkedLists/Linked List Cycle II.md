# Linked List Cycle II  

[Question Link](https://leetcode.com/problems/linked-list-cycle-ii/)  

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def detectCycle(self, head):
        fast = head
        slow = head
        start = head
        
        while fast and fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
            
            if (slow == fast):
                while slow != start:
                    slow = slow.next
                    start = start.next
                return start
            
        return None
```