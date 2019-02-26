# Smallest Range I

[Question Link](https://leetcode.com/problems/smallest-range-i/)  

Given an array A of integers, for each integer A[i] we may choose any x with -K <= x <= K, and add x to A[i].  

After this process, we have some array B.  

Return the smallest possible difference between the maximum value of B and the minimum value of B.  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def smallestRangeI(self, A, K):
        """
        :type A: List[int]
        :type K: int
        :rtype: int
        """        
        maxi = A[0]
        mini = A[0]
        
        for a in A:
            if a > maxi:
                maxi = a
                continue
                
            if a < mini:
                mini = a
                continue
        
        # shrink the range by K by subtracting K from the max and 
        # adding K to the min. 
        answer = (maxi - K) - (mini + K)
        if answer < 0:
        	answer = 0
        
        return answer
```