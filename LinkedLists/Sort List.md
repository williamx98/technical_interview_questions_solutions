# Sort List  

[Question Link](https://leetcode.com/problems/sort-list/)  

Sort a linked list in O(n log n) time using constant space complexity.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def sortList(self, head):
        if not head or not head.next:
            return head
        
        # divide list into two parts
        fast = head.next
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            
        # cut down the first part
        second = slow.next
        slow.next = None
        l = self.sortList(head)
        r = self.sortList(second)

        # get the return node "head"
        def merge(l1, l2):
            l1P = l1
            l2P = l2

            newHead = ListNode(None)
            pointer = newHead

            while l1P or l2P:
                if l1P is None and l2P is not None:
                    pointer.next = l2P
                    break

                if l2P is None and l1P is not None:
                    pointer.next = l1P
                    break

                if l1P is not None and (l2P is None or l1P.val <= l2P.val):
                    pointer.next = l1P
                    l1P = l1P.next
                else:
                    pointer.next = l2P
                    l2P = l2P.next    

                pointer = pointer.next

            return newHead.next
        
        return merge(l, r)
```