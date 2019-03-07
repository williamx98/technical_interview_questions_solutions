# Rotate Image  

[Question Link](https://leetcode.com/problems/rotate-image/)  

You are given an n x n 2D matrix representing an image.  

Rotate the image by 90 degrees (clockwise).  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution:
    def rotate(self, A):
        n = len(A)
        
        for r in xrange(n):
            for c in xrange(r, n):
                temp = A[r][c]
                A[r][c] = A[c][r]
                A[c][r]= temp
                
        for r in xrange(n):
            for c in xrange(n//2):
                temp = A[r][c]
                A[r][c] = A[r][n - 1 - c]
                A[r][n - 1 - c] = temp
```