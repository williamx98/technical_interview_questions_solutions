# Copy List with Random Pointer  

[Question Link](https://leetcode.com/problems/copy-list-with-random-pointer/)  

description

##### Constraints:

### Explanation:
TLDR: 

### Notes:

## Solution:
```Python
class Solution:
    def copyRandomList(self, head):
        dic = dict()
        dic[None] = None
        
        m = head
        while m:
            dic[m] = RandomListNode(m.label)
            m = m.next
        
        m = head
        while m:
            dic[m].next = dic[m.next]
            dic[m].random = dic[m.random]
            m = m.next
        return dic[head]
```

## Solution:
```Python
class Solution(object):
    def copyRandomList(self, head):
        if not head:
            return None
        
        # make a copy of the list by duplicating each node and storing it next to the current node
        p = head
        while p:
            node = RandomListNode(p.label)
            node.next = p.next
            p.next = node
            p = p.next.next
            # p = node.next
            
        # attach the random pointers by using original list's random pointers to set the duplicated's random pointer to be the random pointers duplicate
        p = head    
        while p:
            if p.random:
                p.next.random = p.random.next
            p = p.next.next
        
        # servere the connection between the two lists
        newhead = head.next
        pold = head
        pnew = newhead
        while pnew.next:
            pold.next = pnew.next
            pold = pold.next
            pnew.next = pold.next
            pnew = pnew.next
        pold.next = None
        
        return newhead
```