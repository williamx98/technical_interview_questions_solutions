# Subsets  

[Question Link](https://leetcode.com/problems/subsets/)  

Given a set of distinct integers, nums, return all possible subsets (the power set).

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        answer = []
        
        def permute(currSub, start):
            copy = []
            for item in currSub:
                copy.append(item)
            answer.append(copy)
            
            for index in xrange(start, len(nums)):
                currSub.append(nums[index])
                permute(currSub, index + 1)
                currSub.pop()
            
        permute([], 0)
        
        return answer
```