# Third Maximum Number  

[Question Link](https://leetcode.com/problems/third-maximum-number/)  

Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def thirdMax(self, nums):
        setNums = set(nums)
        if len(setNums) < 3:
            return max(setNums)
        
        answer = [-float('inf'), -float('inf'), -float('inf')]
        for num in setNums:
                if num > answer[0]:   
                    answer = [num, answer[0], answer[1]]
                elif num > answer[1]: 
                    answer = [answer[0], num, answer[1]]
                elif num > answer[2]: 
                    answer = [answer[0], answer[1], num]
        
        return answer[2]
```
