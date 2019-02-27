# Insertion Sort List  

[Question Link](https://leetcode.com/problems/insertion-sort-list/)  

Sort a linked list using insertion sort.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def insertionSortList(self, head):
        dummy = ListNode(0)
        dummy.next = head
        
        p = dummy
        cur = head

        ## traverse to the last second node 
        while cur and cur.next:

            # go foward
            next_val = cur.next.val
            if cur.val <= next_val:
                cur = cur.next 
                continue

            ## if there is an element which is smaller than previous sequence
            ## we need to find a proper postion to insert this small element
            if p.next.val > next_val:
                p = dummy

            ## p stops at the element which is smaller than next_val
            ## eg 1,2,5,6,7,4, 8,9 --> since 4 is bigger than 1, 2
            ## we use p.next.val to compare, hence p would point element 2
            ## update: cur would point at 7
            while p.next.val <= next_val:
                p = p.next 

            # move the found node into position
            new = cur.next
            cur.next = cur.next.next
            new.next = p.next
            p.next = new

        return dummy.next  
```