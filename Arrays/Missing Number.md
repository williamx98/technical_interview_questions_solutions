# Missing Number  

### Rating: [5/5] Good intro into array traversal. Super straight forward and a good first step into number theory.

[Question Link](https://leetcode.com/problems/missing-number/)  

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.  

### Explanation:
TLDR: Expected sum can be calcualted via summation formula. Missing number is the difference between the expected sum and the actual sum of the array.

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