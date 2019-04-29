# Range Addition II  

[Question Link](https://leetcode.com/problems/range-addition-ii/)  

Given an m * n matrix M initialized with all 0's and several update operations.  

Operations are represented by a 2D array, and each operation is represented by an array with two positive integers a and b, which means M[i][j] should be added by one for all 0 <= i < a and 0 <= j < b.  

You need to count and return the number of maximum integers in the matrix after performing all the operations.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def maxCount(self, m, n, ops):
        rowMin = m
        colMin = n
        
        for op in ops:
            row = op[0]
            col = op[1]
            
            if row != 0 and row < rowMin:
                rowMin = row
                
            if col != 0 and col < colMin:
                colMin = col
                
        return rowMin * colMin
```