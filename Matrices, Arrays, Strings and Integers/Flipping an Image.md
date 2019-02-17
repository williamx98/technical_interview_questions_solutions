# Flipping an Image

[Question Link](https://leetcode.com/problems/flipping-an-image/)  

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.  

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].  

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        for row in A:
            left = 0
            right = len(row) - 1
            
            while left <= right:
                if row[left] == row[right]:
                    row[left] = (row[left] + 1) % 2
                    # dont set the right when left == right because its already been flipped
                    if left != right:
                        row[right] = (row[right] + 1) % 2
                
                left = left + 1
                right = right - 1
                
        return A
```
