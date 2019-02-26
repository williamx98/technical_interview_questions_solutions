# 01 Matrix  

[Question Link](https://leetcode.com/problems/01-matrix/)  


Given a matrix consists of 0 and 1, find the distance of the nearest 0 for each cell.  

The distance between two adjacent cells is 1.  

##### Constraints:

### Explanation:
TLDR: Whenever there is a 1, set that cell to max_int. Set it to the minimum between its top and left and then bottom and right cells

### Notes:


## Solution:
```Python
class Solution:
    def updateMatrix(self, matrix):
        m = len(matrix)
        n = len(matrix[0])
        
        for i in xrange(m):
            for j in xrange(n):
                if matrix[i][j] != 0:
                    matrix[i][j] = float("inf")
                    if i > 0 and matrix[i - 1][j] + 1 < matrix[i][j]:
                        matrix[i][j] = matrix[i - 1][j] + 1
                    if j > 0 and matrix[i][j - 1] + 1 < matrix[i][j]:
                        matrix[i][j] = matrix[i][j - 1] + 1
                        
        for i in xrange(m - 1, -1, -1):
            for j in xrange(n - 1, -1, -1):
                if matrix[i][j] != 0:
                    if i + 1 < m and matrix[i + 1][j] + 1 < matrix[i][j]:
                        matrix[i][j] = matrix[i + 1][j] + 1
                    if j + 1 < n and matrix[i][j + 1] + 1 < matrix[i][j]:
                        matrix[i][j] = matrix[i][j + 1] + 1
                        
        return matrix
```