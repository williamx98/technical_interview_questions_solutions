# K Closest Points to Origin

[Question Link]https://leetcode.com/problems/k-closest-points-to-origin/)  

We have a list of points on the plane.  Find the K closest points to the origin (0, 0).  

##### Constraints:

### Explanation:
TLDR: 

### Notes:
Python defaults to a min-heap. We want a max-heap. Make all comparaitves negative to simulate a max-heap. Closer to origin - on bottom. Farthest from origin - on top.

## Solution:
```Python
import heapq 

class Solution(object):
    def kClosest(self, points, K):
        """
        :type points: List[List[int]]
        :type K: int
        :rtype: List[List[int]]
        """
        def calcDist(point):
            a = point[0]
            b = point[1]
            return a * a + b * b
        
        heap = []
        
        for point in points:
            dist = calcDist(point)
            if len(heap) >= K and heap[0][0] < -dist:
                heapq.heappop(heap)
                
            if len(heap) < K :
                heapq.heappush(heap, (-dist, point))
        
        answer = []
        
        for a in heap:
            answer.append(a[1])
        return answer
```