# Transpose Matrix

[Question Link](https://leetcode.com/problems/transpose-matrix/)  

Given a matrix A, return the transpose of A.  

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def transpose(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        answer = []
        
        for colIn in xrange(len(A[0])):
            newRow = []
            for rowIn in xrange(len(A)):
                newRow.append(A[rowIn][colIn])
            answer.append(newRow)
        return answer
```
