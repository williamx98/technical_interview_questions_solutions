# Longest Continuous Increasing Subsequence  

## Rating: [5/5] Good question. Simple solution.

[Question Link](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)  

Given an unsorted array of integers, find the length of longest continuous increasing subsequence (subarray).  

### Explanation:
TLDR: Add to length on each increase between indexes. Reset to 1 on a decrease.


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
        
        counter = 1
        maximum = 1
        prevNum = nums[0]
        
        for num in nums:
            if prevNum < num:
                counter += 1

                if counter > maximum:
                    maximum = counter
            else:
                counter = 1
                
            prevNum = num
            
        return maximum
        
```