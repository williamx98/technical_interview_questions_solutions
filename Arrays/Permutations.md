# Permutations  

[Question Link](https://leetcode.com/problems/permutations/)  

Given a collection of distinct integers, return all possible permutations.

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        answer = []
        
        def permute(currPerm, permIndex, used):
            if permIndex >= len(currPerm):
                copy = []
                for item in currPerm:
                    copy.append(item)
                answer.append(copy)
                
            for index, num in enumerate(nums):
                if index in used: continue
                currPerm[permIndex] = nums[index]
                used.add(index)
                permute(currPerm, permIndex + 1, used)
                used.remove(index)
        
        perm = [0] * len(nums)
        permute(perm, 0, set())
        
        return answer
```