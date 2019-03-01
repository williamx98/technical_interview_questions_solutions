# Move Zeroes  

[Question Link](https://leetcode.com/problems/move-zeroes/)  

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.  

### Explanation:
TLDR: Swap zeros with non-zeros until they are grouped together and will "shift" down to the end

## Solution:
```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """

        # index represents the last index of a zero
        # skipSize represents the distance from the zero to check for values
        # increase the skip size everytime you find a zero
        # set the current index to the non-zero value
        # set the non-zero value index to zero
        skipSize = 0
        index = 0
        
        while index + skipSize < len(nums):
            if nums[index + skipSize] == 0:
                skipSize += 1
                continue
            
            nums[index] = nums[index + skipSize]
            if skipSize > 0:
                nums[index + skipSize] = 0
            index += 1
            
```
