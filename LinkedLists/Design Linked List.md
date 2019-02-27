# Design Linked List  

[Question Link](https://leetcode.com/problems/design-linked-list/)  

description

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class MyLinkedList(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.data = [None] * 1998
        self.head = 999
        self.size = 0
    def get(self, index):
        """
        Get the value of the index-th node in the linked list. If the index is invalid, return -1.
        :type index: int
        :rtype: int
        """
        if index + 1 > self.size:
            return -1
        
        return self.data[self.head + index] 
        

    def addAtHead(self, val):
        """
        Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
        :type val: int
        :rtype: void
        """
        self.head -= 1
        self.data[self.head] = val
        self.size += 1

    def addAtTail(self, val):
        """
        Append a node of value val to the last element of the linked list.
        :type val: int
        :rtype: void
        """
        self.data[self.head + self.size] = val
        self.size += 1
        

    def addAtIndex(self, index, val):
        """
        Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted.
        :type index: int
        :type val: int
        :rtype: void
        """
        if index > self.size:
            return
        
        self.data.insert(self.head + index, val)
        self.size += 1
        

    def deleteAtIndex(self, index):
        """
        Delete the index-th node in the linked list, if the index is valid.
        :type index: int
        :rtype: void
        """
        if index >= self.size:
            return
        
        self.data.pop(self.head + index)
        self.data.append(None)
        self.size -= 1
        
        


# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```