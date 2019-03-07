# Missing Number  

[Question Link](https://leetcode.com/problems/missing-number/)  

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        total = 0
        for num in nums:
            total += num
            
        n = len(nums)
        expected = (n * (n + 1))//2
        
        return expected - total
```