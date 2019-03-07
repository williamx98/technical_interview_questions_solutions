# Number of 1 Bits  

[Question Link](https://leetcode.com/problems/number-of-1-bits/)  

Write a function that takes an unsigned integer and return the number of '1' bits it has (also known as the Hamming weight).  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n: int
        :rtype: int
        """
        total = 0
        
        while n != 0:
            total += n & 0x1
            n = n >> 1
        
        return total
```