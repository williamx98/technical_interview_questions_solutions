# Fibonacci Number

[Question Link](https://leetcode.com/problems/fibonacci-number/)  

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def fib(self, N):
        """
        :type N: int
        :rtype: int
        """
        dp = [0,1]
        
        if (N < 2):
            return dp[N]
        
        for n in range(2, N + 1):
            prev = dp[1]
            dp[1] = dp[0] + dp[1]
            dp[0] = prev
            
        return dp[1]
        
```