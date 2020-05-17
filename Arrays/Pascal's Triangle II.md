# Pascal's Triangle II  

### Rating: [4/5] Good Question. Not impossible but hard to find optimal solution.

[Question Link](https://leetcode.com/problems/pascals-triangle-ii/)  

Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle.  

Note that the row index starts from 0.  

### Explanation:

## Solution:
```Python
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """

        # base case
        if rowIndex == 0:
            return [1]

        # make an empty answer array. 
        answerArray = [0] * (rowIndex + 1)
        # make the first element 1
        answerArray[0] = 1
        
        # run throught each row
        for currentRow in xrange(1, rowIndex + 1):
            # going backwards, calculate the value for each index
            for index in xrange(currentRow, 0, -1):
                answerArray[index] += answerArray[index - 1]

        return answerArray
```