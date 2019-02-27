# Merge k Sorted Lists  

[Question Link](https://leetcode.com/problems/merge-k-sorted-lists/)  

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.  

##### Constraints:

### Explanation:
TLDR: Compare only the front of each list and store tem in a heap. Use the heap to maintain the smallest availible item.

### Notes:


## Solution:
```Python
import heapq

class Solution(object):
    def mergeKLists(self, lists):
        
        if not lists:
            return None
        
        dummyHead = ListNode(0)
        answerPointer = dummyHead
        queue = []
        
        for index,item in enumerate(lists):
            if item:
                heapq.heappush(queue, (item.val, index, item))
                
        while queue:
            _, index, nodeToAdd = heapq.heappop(queue)

            answerPointer.next = nodeToAdd
            answerPointer = nodeToAdd

            lists[index] = lists[index].next

            if lists[index]:
                heapq.heappush(queue, (lists[index].val, index, lists[index]))

        return dummyHead.next
```