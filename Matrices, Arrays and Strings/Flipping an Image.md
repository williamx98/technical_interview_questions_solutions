# Flipping an Image

[Question Link](https://leetcode.com/problems/flipping-an-image/)  

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.  

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].  

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution With Comments:
```Python
class Solution(object):
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        flippedMatrix = []
        
        for row in A:
            flippedRow = []
            for col in row[::-1]:
                if col == 1:
                    flippedRow.append(0)
                else:
                    flippedRow.append(1)
            flippedMatrix.append(flippedRow)
        return flippedMatrix
```
