# Design Circular Queue

[Question Link](https://leetcode.com/explore/featured/card/queue-stack/228/first-in-first-out-data-structure/1337/)  

Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".  

One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.  

Your implementation should support following operations:  

MyCircularQueue(k): Constructor, set the size of the queue to be k.  
Front: Get the front item from the queue. If the queue is empty, return -1.  
Rear: Get the last item from the queue. If the queue is empty, return -1.  
enQueue(value): Insert an element into the circular queue. Return true if the operation is successful.  
deQueue(): Delete an element from the circular queue. Return true if the operation is successful.  
isEmpty(): Checks whether the circular queue is empty or not.  
isFull(): Checks whether the circular queue is full or not.  

##### Constraints:
All values will be in the range of [0, 1000].  
The number of operations will be in the range of [1, 1000].  
Please do not use the built-in Queue library.  

### Explanation:
TLDR: 

### Notes:


## Solution With Comments:
```Python
class MyCircularQueue(object):

    def __init__(self, k):
        """
        Initialize your data structure here. Set the size of the queue to be k.
        :type k: int
        """
        self.length = k
        self.data = [None] * k
        self.headIn = 0
        self.endIn = -1
        self.size = 0

    def enQueue(self, value):
        """
        Insert an element into the circular queue. Return true if the operation is successful.
        :type value: int
        :rtype: bool
        """
        if self.isFull():
            return False

        self.endIn = (self.endIn + 1) % self.length
        self.data[self.endIn] = value
        self.size += 1
        return True
        
    def deQueue(self):
        """
        Delete an element from the circular queue. Return true if the operation is successful.
        :rtype: bool
        """
        if self.isEmpty():
            return False
        
        self.headIn = (self.headIn + 1) % self.length
        self.size -= 1
        return True

    def Front(self):
        """
        Get the front item from the queue.
        :rtype: int
        """
        if self.isEmpty():
            return -1
        
        return self.data[self.headIn]

    def Rear(self):
        """
        Get the last item from the queue.
        :rtype: int
        """
        if self.isEmpty():
            return -1
        
        return self.data[self.endIn]

    def isEmpty(self):
        """
        Checks whether the circular queue is empty or not.
        :rtype: bool
        """
        return self.size == 0
    
    def isFull(self):
        """
        Checks whether the circular queue is full or not.
        :rtype: bool
        """
        return self.size == self.length
```

## Solution Without Comments:
```Python
class MyCircularQueue(object):

    def __init__(self, k):
        self.length = k
        self.data = [None] * k
        self.headIn = 0
        self.endIn = -1
        self.size = 0

    def enQueue(self, value):
        if self.isFull():
            return False

        self.endIn = (self.endIn + 1) % self.length
        self.data[self.endIn] = value
        self.size += 1
        return True
        
    def deQueue(self):
        if self.isEmpty():
            return False
        
        self.headIn = (self.headIn + 1) % self.length
        self.size -= 1
        return True

    def Front(self):
        if self.isEmpty():
            return -1
        
        return self.data[self.headIn]

    def Rear(self):
        if self.isEmpty():
            return -1
        
        return self.data[self.endIn]

    def isEmpty(self):
        return self.size == 0
    
    def isFull(self):
        return self.size == self.length
```