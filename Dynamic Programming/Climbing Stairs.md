# https://leetcode.com/problems/climbing-stairs/

[Question Link](https://leetcode.com/problems/climbing-stairs/)  

You are climbing a stair case. It takes n steps to reach to the top.  

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?  

Note: Given n will be a positive integer.  

##### Constraints:

### Explanation:
TLDR: Its essentially a variation of fibonacci.

Starting from the smallest case, what if there were only zero steps? Then there would be only 1 way to go from... here to here. Just like an empty set is a subset, choosing not to take a step is still technically a step. Regardless of how you view, the pattern is the number of steps to reach a stair case of n steps is the the total of the number of steps to reach a stair case of n - 1 steps plus the number of steps to reach a stair case of n - 2.  If you choose to view a zero height staircase as 0 steps, then the answer has an additional plus 1.  

### Notes:


## Solution:
```Python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0:
            return 1
        
        last2 = 1
        last1 = 1
        
        for i in range(2, n + 1):
            temp = last2 + last1
            last2 = last1
            last1 = temp
        
        return last1
```