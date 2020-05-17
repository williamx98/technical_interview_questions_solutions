# Contains Duplicate  

### Rating: [5/5] Good intro into arrays and set. Straight foward question, straight foward solution.

[Question Link](https://leetcode.com/problems/contains-duplicate/)  

Given an array of integers, find if the array contains any duplicates.  

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.  

### Explanation:
TLDR: Use a set to track existence of seen values.

## Solution:
```Python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        seen = set()
        
        for num in nums:
            if num in seen:
                return True
            else:
                seen.add(num)
                
        return False
```
