# Two Sum II - Input array is sorted  

[Question Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)  

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.  

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        left = 0
        right = len(numbers) - 1
        
        while left < right:
            total = numbers[left] + numbers[right]
            if total == target:
                return [left + 1, right + 1]
                # TODO: increment final answer indexes by 1
            elif total > target:
                right = right - 1
            # if not above, will be below
            elif total < target:
                left = left + 1
        
        # shouldn't get here
        return []
```