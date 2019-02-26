# 3Sum  

[Question Link](https://leetcode.com/problems/3sum/)  

Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.  

##### Constraints:

### Explanation:
TLDR: Sort the list. choose a central point. Move indexes left and right of that point. Move the left index up to increase the sum. Move the right index down to decrease the sum. No duplicates allowed to once an answer has been found, move the left and right pointer until they are pointer at new values.  

### Notes:


## Solution:
```Python
class Solution(object):
    def threeSum(self, nums):
        res = []
        nums.sort()
        
        for i in xrange(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l = i+1
            r = len(nums)-1
            
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if s < 0:
                    l +=1 
                elif s > 0:
                    r -= 1
                else:
                    res.append((nums[i], nums[l], nums[r]))
                    while l < r and nums[l] == nums[l+1]:
                        l += 1
                    while l < r and nums[r] == nums[r-1]:
                        r -= 1
                    
                    l += 1
                    r -= 1
        return res
```