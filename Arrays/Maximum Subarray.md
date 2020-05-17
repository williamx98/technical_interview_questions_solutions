# Maximum Subarray  

### Rating: [5/5] Good intro into array traversal. Super straight forward and a good first step into number theory.

[Question Link](https://leetcode.com/problems/maximum-subarray/)  

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.  

### Explanation:
TLDR: Add the previous element if its greater than zero. repeat and look for a max after completion.

Basically, don't ever add a negative number if you want the total to keep increasing. Thus, when you encounter a negative number, reset the counter to 0 after seeing if the counter is a possible answer.

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

### Keep track of the length of the total
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