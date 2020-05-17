# Move Zeroes  

### Rating: [4/5] Good intro into array traversal. Not straight forward answer but also not complicated.

[Question Link](https://leetcode.com/problems/move-zeroes/)  

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.  

### Explanation:
TLDR: Swap zeros with non-zeros until they are grouped together and will "shift" down to the end

keep track of how many zeros we have seen and keep track of where the next element should appear.
Swap elements on every turn that we find a non-zero element.

## Solution:
```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        numOfZerosSeen = 0
        indexToInsertAt = 0
        
        while indexToInsertAt + numOfZerosSeen < len(nums):
            # we saw a zero, don't move the indexToInsertAt
            if nums[indexToInsertAt + numOfZerosSeen] == 0:
                numOfZerosSeen += 1
            else: # we found a non-zero element, swap with the indexToInsertAt
                temp = nums[indexToInsertAt]
                nums[indexToInsertAt] = nums[indexToInsertAt + numOfZerosSeen]
                nums[indexToInsertAt + numOfZerosSeen] = temp

                indexToInsertAt += 1     
```
