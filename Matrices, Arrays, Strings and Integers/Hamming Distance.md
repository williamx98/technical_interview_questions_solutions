# Hamming Distance

[Question Link](https://leetcode.com/problems/hamming-distance/)  

The Hamming distance between two integers is the number of positions at which the corresponding bits are different.  

Given two integers x and y, calculate the Hamming distance.  


##### Constraints:

### Explanation:
TLDR: Get all bits to be counted through exclusive-or and count every time the number becomes odd on every division

### Notes:


## Solution:
```Python
class Solution(object):
    def hammingDistance(self, x, y):
        """
        :type x: int
        :type y: int
        :rtype: int
        """
        z = x ^ y
        answer = 0
        while z > 0:
            answer = answer + z % 2
            z = z >> 1
            
        return answer
```