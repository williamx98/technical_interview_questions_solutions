# Product of Array Except Self  

[Question Link](https://leetcode.com/problems/product-of-array-except-self/)  

Given an array nums of n integers where n > 1,  return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution:
    def productExceptSelf(self, nums):
        limit = len(nums)
        output = []
        
        prev = 1
        for i in range(0,limit):
            output.append(prev)
            prev = prev * nums[i]
        
        prev = 1
        for i in range(limit - 1, -1, -1):
            output[i] = output[i] * prev
            prev = prev * nums[i]
            
        return output
```
