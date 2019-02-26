# Binary Gap  

[Question Link](https://leetcode.com/problems/binary-gap/)  

Given a positive integer N, find and return the longest distance between two consecutive 1's in the binary representation of N.  

If there aren't two consecutive 1's, return 0.  

##### Constraints:

### Explanation:
TLDR: Add zero until a 1 is found. Then add 1 until 1 found. When 1 found, keep the greater between the last result and the current result.

### Notes:


## Solution:
```Python
class Solution(object):
    def binaryGap(self, N):
        """
        :type N: int
        :rtype: int
        """
        res = 0
        d = 0
        found = 0
        
        while N > 0:
            if N % 2 == 1:
                res = max(res, d)
                d = 0
                found = 1
                
            d += found
            N = N // 2
            
        return res
```