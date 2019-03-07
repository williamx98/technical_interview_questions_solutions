# Top K Frequent Elements  

[Question Link](https://leetcode.com/problems/top-k-frequent-elements/)  

Given a non-empty array of integers, return the k most frequent elements.

##### Constraints:

### Explanation:
TLDR: Default implementation of Python heap is a min-heap. Min-heaps with a set size will store the top k largest elements in order from least to greated.

### Notes:


## Solution:
```Python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        heap = []
        map = {}
        
        for num in nums:
            if num not in map:
                map[num] = 0
                
            map[num] += 1
            
        for num in map:
            freq = map[num]
            
            if len(heap) >= k and freq > heap[0][0]:
                heapq.heappop(heap)
                
            if len(heap) < k:
                heapq.heappush(heap, (freq, num))
                
        answer = []
        
        while heap:
            answer.append(heapq.heappop(heap)[1])
            
        return answer
```