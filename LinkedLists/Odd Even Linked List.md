# Odd Even Linked List  

[Question Link](https://leetcode.com/problems/odd-even-linked-list/)  

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.  

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def oddEvenList(self, head):
        if head is None:
            return head
        
        even = head
        oddHead = ListNode(None)
        odd = oddHead
        odd.next = ListNode(None)
        
        while odd and odd.next:
            odd.next = even.next
            odd = even.next
            
            if even.next:
                even.next = even.next.next
                
            if even.next:
                even = even.next
                
        even.next = oddHead.next
        
        return head
```