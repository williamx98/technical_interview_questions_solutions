# Add Two Numbers  

[Question Link](https://leetcode.com/problems/add-two-numbers/)  

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.  

You may assume the two numbers do not contain any leading zero, except the number 0 itself.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        carry = 0
        root = ListNode(0)
        n = root
        
        while l1 or l2 or carry:
            total = carry
            if l1:
                total += l1.val
                l1 = l1.next
            if l2:
                total += l2.val
                l2 = l2.next
            
            carry = total // 10
            val = total % 10
            
            n.next = ListNode(val)
            n = n.next
        return root.next
```
