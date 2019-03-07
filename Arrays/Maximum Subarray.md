# Maximum Subarray  

[Question Link](https://leetcode.com/problems/maximum-subarray/)  

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.  

##### Constraints:

### Explanation:
TLDR: Add the previous element if its greater than zero. repeat and look for a max after completion

### Notes:

## Solution:
```Python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        answer = None
        tempTotal = 0
        
        for index in xrange(len(nums)):
            num = nums[index]
            tempTotal += num
            
            if answer is None or tempTotal > answer:
                answer = tempTotal
            
            if tempTotal < 0:
                tempTotal = 0
                
        return answer
```

## Solution:
```Python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        answer = None
        tempTotal = 0
        tempStart = 0
        start = 0
        end = 0
        
        for index in xrange(len(nums)):
            num = nums[index]
            tempTotal += num
            
            if answer == None or tempTotal > answer:
                answer = tempTotal
                start = tempStart
                end = index
            
            if tempTotal < 0:
                tempTotal = 0
                tempStart = index + 1
                
        return answer
```

## Solution:
```Python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        max = nums[0]
        for index in xrange(1, len(nums)):
            if nums[index - 1] > 0:
                nums[index] += nums[index - 1]
                
            if nums[index] > max:
                max = nums[index]
        
        return max
```