# Flatten a Multilevel Doubly Linked List  

[Question Link](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)  

You are given a doubly linked list which in addition to the next and previous pointers, it could have a child pointer, which may or may not point to a separate doubly linked list. These child lists may have one or more children of their own, and so on, to produce a multilevel data structure, as shown in the example below.  

Flatten the list so that all the nodes appear in a single-level, doubly linked list. You are given the head of the first level of the list.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def flatten(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        def flatten(node):
            tail = node
            while node is not None:
                if node.child is not None:
                    child = node.child
                    node.child = None
                    next = node.next
                    
                    node.next = child
                    child.prev = node
                    
                    endOfChild = flatten(child)
                    endOfChild.next = next
                    if next is not None:
                        next.prev = endOfChild
                    
                    tail = endOfChild
                    node = next
                else:
                    tail = node
                    node = node.next
                
            return tail
        
        flatten(head)
        return head
```