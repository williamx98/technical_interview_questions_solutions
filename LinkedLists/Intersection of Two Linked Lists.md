# Intersection of Two Linked Lists  

[Question Link](https://leetcode.com/problems/intersection-of-two-linked-lists/)  

Write a program to find the node at which the intersection of two singly linked lists begins.  

##### Constraints:

### Explanation:
TLDR: When the lists are the same "size", they will intersect before reaching the end of themselves. If they are not the same size, the shorter list iterator traverses down the longer list. Once the longer list iterator swaps over to the shorter list, they will both start at the same disctance from the intersection point.  

### Notes:


## Solution:
```Python
class Solution:
    # @param two ListNodes
    # @return the intersected ListNode
    def getIntersectionNode(self, headA, headB):
        if headA is None or headB is None:
            return None

        pa = headA # 2 pointers
        pb = headB

        while pa is not pb:
            if pa is None:
                pa = headB
            else:
                pa = pa.next
            
            if pb is None:
                pb = headA
            else:
                pb = pb.next

        return pa
```