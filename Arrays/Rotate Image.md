# Rotate Image  

[Question Link](https://leetcode.com/problems/rotate-image/)  

You are given an n x n 2D matrix representing an image.  

Rotate the image by 90 degrees (clockwise).  

##### Constraints:

### Explanation:
TLDR: This is a basic row-col swap. The matrix is N X N so its a straight row to column swap. 

### Notes:
```base matrix```
[1,2]
[3,4]

```step 1: swap rows and cols```
[1,3]
[2,4]


```step2: reverse each row```
[3,1]
[4,2]

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
