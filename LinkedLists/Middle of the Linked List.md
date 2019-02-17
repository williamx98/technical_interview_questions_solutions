# Middle of the Linked List

[Question Link](https://leetcode.com/problems/middle-of-the-linked-list/)  

Given a non-empty, singly linked list with head node head, return a middle node of linked list.  

If there are two middle nodes, return the second middle node.  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def middleNode(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        slow = head
        fast = head
        
        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
        
        return slow      
```