# Reverse Nodes in k-Group  

[Question Link](https://leetcode.com/problems/reverse-nodes-in-k-group/)  

Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.  

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object): 
    def reverseKGroup(self, head, k):
        dummy = ListNode(0)
        jump = dummy
        r = head
        l = head
        dummy.next = head

        while True:
            count = 0
            while r and count < k:   # use r to locate the range
                r = r.next
                count += 1

            if count != k:
            	return dummy.next

            pre = r
            cur = l
            for _ in range(k):
                oldNext = cur.next
                cur.next = pre
                pre = cur
                cur = oldNext
            
            jump.next = pre
            jump = l
            l = r
```