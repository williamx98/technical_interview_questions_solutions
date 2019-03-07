# Kth Largest Element in an Array  

[Question Link](https://leetcode.com/problems/kth-largest-element-in-an-array/)  

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def findKthLargest(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        heap = []
        
        for num in nums:
            if len(heap) >= k and num > heap[0]:
                heapq.heappop(heap)
                
            if len(heap) < k:
                heapq.heappush(heap, num)
                
        return heapq.heappop(heap)
```