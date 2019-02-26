# Partition List  

[Question Link](https://leetcode.com/problems/partition-list/)  

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.  

You should preserve the original relative order of the nodes in each of the two partitions.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def partition(self, head, x):
        greaterThanEqualHead = ListNode(0)
        lessThanHead = ListNode(0)
        
        gPointer = greaterThanEqualHead
        lPointer = lessThanHead
        hPointer = head
        
        while hPointer is not None:
            hNext = hPointer.next
            if hPointer.val >= x:
                gPointer.next = hPointer
                gPointer = gPointer.next
            else:
                lPointer.next = hPointer
                lPointer = lPointer.next
                
            hPointer = hNext
        
        gPointer.next = None
        lPointer.next = greaterThanEqualHead.next
            
        return lessThanHead.next
```