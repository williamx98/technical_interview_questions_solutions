# Number Complement  

[Question Link](https://leetcode.com/problems/number-complement/)  

Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.  

##### Constraints:

### Explanation:
TLDR: Make bit mask and exclusive-or with given num

### Notes:


## Solution:
```Python
class Solution(object):
    def findComplement(self, num):
        i = 1
        while i <= num:
            i = i << 1
        return (i - 1) ^ num
```