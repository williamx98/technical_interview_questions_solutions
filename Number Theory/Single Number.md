# Single Number  

[Question Link](https://leetcode.com/problems/single-number/)  

Given a non-empty array of integers, every element appears twice except for one. Find that single one.  

Note:  

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        total = 0
        expected = 0
        for num in nums:
            total += num
            
        for num in set(nums):
            expected += num * 2
            
        return expected - total
```