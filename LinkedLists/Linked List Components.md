# Linked List Components  

[Question Link](https://leetcode.com/problems/linked-list-components/)  

***This is a terrible problem description***

We are given head, the head node of a linked list containing unique integer values.  

We are also given the list G, a subset of the values in the linked list.  

Return the number of connected components in G, where two values are connected if they appear consecutively in the linked list.  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def numComponents(self, head, G):
        setG = set(G)
        res = 0
        while head:
            if head.val in setG and (head.next == None or head.next.val not in setG):
                res += 1
            head = head.next
        return res
```