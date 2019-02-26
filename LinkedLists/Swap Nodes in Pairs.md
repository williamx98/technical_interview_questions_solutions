# Swap Nodes in Pairs  

[Question Link](https://leetcode.com/problems/swap-nodes-in-pairs/)  

Given a linked list, swap every two adjacent nodes and return its head.  

You may not modify the values in the list's nodes, only nodes itself may be changed.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def swapPairs(self, head):
        if head is None or head.next is None:
            return head;
        
        first = head
        newHead = first.next
        prev = None
        
        while first and first.next:
            second = first.next
            third = second.next
            
            if prev:
                prev.next = second
            
            second.next = first
            first.next = third
            prev = first
            first = third
        
        return newHead
```