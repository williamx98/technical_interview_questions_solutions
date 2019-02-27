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
class Solution:
    def addTwoNumbers(self, l1, l2):
        stack1 = []
        stack2 = []
        p1 = l1
        p2 = l2
        
        while p1:
            stack1.append(p1.val)
            p1 = p1.next
            
        while p2:
            stack2.append(p2.val)
            p2 = p2.next
            
        currentHead = None
        rem = 0
        while stack1 or stack2 or rem:
            s = rem
            if stack1:
                s += stack1.pop()
                
            if stack2:
                s += stack2.pop()
            
            rem = s // 10
            toAdd = ListNode(s % 10)
            toAdd.next = currentHead
            currentHead = toAdd
            
        return currentHead
```

## Solution:
```Python
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        def reverse(head):
            if head is None or head.next is None:
                return head
        
            newHead = None
            current = head
            while current:
                oldNext = current.next
                current.next = newHead
                newHead = current
                current = oldNext
            
            return newHead
        
        
        l1 = reverse(l1)
        l2 = reverse(l2)

        carry = 0
        root = ListNode(0)
        n = root
        
        while l1 or l2 or carry:
            v1 = 0
            v2 = 0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
            
            total = v1+v2+carry
            carry = total // 10
            val = total % 10
            
            n.next = ListNode(val)
            n = n.next
        
        return reverse(root.next)
```