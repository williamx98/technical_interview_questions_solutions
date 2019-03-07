# Majority Element  

[Question Link](https://leetcode.com/problems/majority-element/)  

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.  

You may assume that the array is non-empty and the majority element always exist in the array.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = 1
        res = nums[0]
        for i in range(1, len(nums)):
            if count == 0:
                res = nums[i]
            
            if res == nums[i]:
                count += 1
            else:
                count -= 1
        return res
```