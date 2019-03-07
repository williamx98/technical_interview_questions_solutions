# Pascal's Triangle  

[Question Link](https://leetcode.com/problems/pascals-triangle/)  

Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        answer = []
        prevRow = None
        for row in xrange(numRows):
            newRow = []
            for index in xrange(row + 1):
                if index == 0 or index == row:
                    newRow.append(1)
                else:
                    newRow.append(prevRow[index] + prevRow[index - 1])
                    
            prevRow = newRow
            answer.append(newRow)
                    
        return answer
```