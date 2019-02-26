# 1-bit and 2-bit Characters  

[Question Link](https://leetcode.com/problems/1-bit-and-2-bit-characters/)  

We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11).  

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.  

##### Constraints:

### Explanation:
TLDR: Whenever you see a one, make that into a 2bit character so increment the index by 2, otherwise, its a one bit character so increment by 1. If you stop at the last index, that means you have a one-bit character at the end

### Notes:


## Solution:
```Python
class Solution(object):
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        i = 0
        while i < len(bits) - 1:
            if bits[i] == 1:
                i += 1
            i += 1
            
        if i == len(bits) - 1:
            return True
        
        return False
```