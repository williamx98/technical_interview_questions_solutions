# Longest Continuous Increasing Subsequence  

[Question Link](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)  

Given an unsorted array of integers, find the length of longest continuous increasing subsequence (subarray).  

##### Constraints:

### Explanation:
TLDR: Keep track of the start of the current increasing subsequence. 

### Notes:


## Solution:
```Python
class Solution(object):
    def findLengthOfLCIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) < 1:
            return 0
        
        start = 0
        maxLength = 0
        
        for index in xrange(1, len(nums)):
            if nums[index] > nums[index - 1]:
                if index - start > maxLength:
                    maxLength = index - start
            elif nums[index] <= nums[index - 1]:
                start = index
            
        return maxLength + 1
```