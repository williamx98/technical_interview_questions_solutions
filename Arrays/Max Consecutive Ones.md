# Max Consecutive Ones  

[Question Link](https://leetcode.com/problems/max-consecutive-ones/)  

Given a binary array, find the maximum number of consecutive 1s in this array.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def findMaxConsecutiveOnes(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = 0
        big = 0
        for num in nums:
            if num == 1:
                count += 1
            else:
                count = 0
            
            big = max(big, count)
        
        return big
```