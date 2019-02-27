# Toeplitz Matrix  

[Question Link](https://leetcode.com/problems/toeplitz-matrix/)  

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.  

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.  

##### Constraints:

### Explanation:
TLDR: Check the next row down only and compare to the next col right only

### Notes:


## Solution:
```Python
class Solution(object):
    def isToeplitzMatrix(self, matrix):
            for row in range(len(matrix) - 1):
                for col in range(len(matrix[0]) - 1):
                    if matrix[row][col] != matrix[row + 1][col + 1]:
                        return False
            return True
```