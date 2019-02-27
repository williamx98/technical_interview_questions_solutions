# Split Linked List in Parts  

[Question Link](https://leetcode.com/problems/split-linked-list-in-parts/)  

Given a (singly) linked list with head node root, write a function to split the linked list into k consecutive linked list "parts".  

The length of each part should be as equal as possible: no two parts should have a size differing by more than 1. This may lead to some parts being null.  

The parts should be in order of occurrence in the input list, and parts occurring earlier should always have a size greater than or equal parts occurring later.  

Return a List of ListNode's representing the linked list parts that are formed.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def splitListToParts(self, root, k):
        
        # find length of the list
        n = 0
        curr = root
        while curr != None:
            n += 1
            curr = curr.next

        # determine part length and any leftover length
        length = n / k
        leftover_length = n % k
        
        # go through list and add to answer list
        curr = root
        parts = []
        for i in xrange(k):
            
            # make a new sublist. add up to length items
            part = []
            for j in xrange(length):
                part.append(curr.val)
                curr = curr.next
            
            # add another item if there was a leftover remainder from before
            if leftover_length > 0:
                part.append(curr.val)
                curr = curr.next
                leftover_length -= 1
                
            parts.append(part)
            
        return parts
```