# Array Partition I
### Rating: [2/5] Good intro to arrays. Useless for learning unless you're an absolute beginner.
[Question Link](https://leetcode.com/problems/array-partition-i/)  

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.    

### Explanation:
TLDR: Sort and add every other one

## Solution:
```Python
class Solution(object):
    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums.sort()
        total = 0
        for num in nums[::2]:
            total += num
            
        return total
```
