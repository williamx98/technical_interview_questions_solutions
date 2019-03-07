# Spiral Matrix II  

[Question Link](https://leetcode.com/problems/spiral-matrix-ii/)  

Given a positive integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        insertNum = 1
        limit = n * n;
        
        mat = [None] * n
        for index in range(n):
            mat[index] = [None] * n
        

        row = 0
        col = 0
        
        left = 0
        right = n - 1
        top = 0
        down = n - 1
        row_direction = 0
        col_direction = 1
        
        
        
        while insertNum <= limit:
            mat[row][col] = insertNum
            insertNum += 1
            
            row += row_direction
            col += col_direction
            
            if col > right:
                col = right
                top += 1
                row_direction = 1
                col_direction = 0
                row += 1
            elif row > down:
                row = down
                right -= 1
                row_direction = 0
                col_direction = -1
                col -= 1
            elif col < left:
                col = left
                down -= 1
                row_direction = -1
                col_direction = 0
                row -= 1
            elif row < top:
                row = top
                left += 1
                row_direction = 0
                col_direction = 1
                col += 1
        
        return mat
```