# Remove Element  

[Question Link](https://leetcode.com/problems/remove-element/)  

Given an array nums and a value val, remove all instances of that value in-place and return the new length.  

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.  

The order of elements can be changed. It doesn't matter what you leave beyond the new length.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        skipSize = 0
        index = 0
        
        while index + skipSize < len(nums):
            if nums[index + skipSize] == val:
                skipSize += 1
            else:
                nums[index] = nums[index + skipSize]
                index += 1
        
        return index
```