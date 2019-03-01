# Reshape the Matrix  

[Question Link](https://leetcode.com/problems/reshape-the-matrix/)  

In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.  

You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.  

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.  

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def matrixReshape(self, nums, r, c):
        """
        :type nums: List[List[int]]
        :type r: int
        :type c: int
        :rtype: List[List[int]]
        """
        if len(nums) * len(nums[0]) != r * c:
            return nums
        
        
        answer = []
        for _ in xrange(r):
            answer.append([0] * c)
        
        for pos in xrange(r*c):
            numsRow = pos // len(nums[0])
            numsCol = pos % len(nums[0])
                
            rRow = pos // c
            cCol = pos % c
            
            answer[rRow][cCol] = nums[numsRow][numsCol]
        
        return answer
```
