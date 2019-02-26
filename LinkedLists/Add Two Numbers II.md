# Add Two Numbers II  

[Question Link](https://leetcode.com/problems/add-two-numbers-ii/)  

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.  

You may assume the two numbers do not contain any leading zero, except the number 0 itself.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        l1Val = 0
        l2Val = 0
        
        while l1:
            l1Val = l1Val * 10 + l1.val
            l1 = l1.next
        
        while l2:
            l2Val = l2Val * 10 + l2.val
            l2 = l2.next
        
        total = l1Val + l2Val
        
        prev = None
        
        if total is 0:
            return ListNode(0)
        
        while total > 0:
            node = ListNode(total % 10)
            node.next = prev
            prev = node
            total //= 10
        
        return prev
```