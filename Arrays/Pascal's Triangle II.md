# Pascal's Triangle II  

[Question Link](https://leetcode.com/problems/pascals-triangle-ii/)  

Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle.  

Note that the row index starts from 0.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        answer = [0] * (rowIndex + 1)
        if rowIndex == 0:
            return [1]
        
        for row in xrange(1, rowIndex + 2):
            prev = 1
            for index in xrange(1, row - 1):
                total = answer[index] + prev
                prev = answer[index]
                answer[index] = total
            answer[row - 1] = 1
            
        return answer
```