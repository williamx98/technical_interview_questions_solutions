# Reverse Bits  

[Question Link](https://leetcode.com/problems/reverse-bits/)  

Reverse bits of a given 32 bits unsigned integer.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:

## Solution:
```Python
class Solution:
    # @param n, an integer
    # @return an integer
    def reverseBits(self, n):
        # base case
        if n == 0:
            return 0
        
        # figure out how many zeros to left shift the final answer by (== the number of conseuctive zeros starting on the left)
        # in     00000010100101000001111010011100
        # get    ^^^^^^ zeros == 6
        leftShift = 0
        while ((n << leftShift) & 0xffffffff) >> leftShift == n:
            leftShift += 1

        # perform the reversal
        answer = 0
        while n > 0:
            rightMost = n & 0x1
            answer = answer << 1
            answer = answer | rightMost
            n = n >> 1
        
        #shift answer left to accomodate for the leftmost zeros in the input
        while leftShift > 1:
            answer = answer << 1
            leftShift -= 1
        
        # mask with 32 bits to clean up the answer
        return answer
```