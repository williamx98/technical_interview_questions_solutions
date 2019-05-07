# Single Number  

[Question Link](https://leetcode.com/problems/single-number/)  

Given a non-empty array of integers, every element appears twice except for one. Find that single one.  

Note:  

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?  

### Explanation:
TLDR: This solution relis on a bit manipulation trick. An number XOR with itself produces 0. If every value in an array were duplicated, and every value in the array were XOR with 0 then that answer, then the final answer would be 0. Because only one value is not duplicated i.e appears once, XOR the entire array with 0 will produce the answer.  
```Given: [2,1,2]```  
```2 XOR 0 = 2```  
```1 XOR 2 = 3```  
```2 XOR 3 = 1```  
```Answer: 1```  

## Solution:
```Python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        answer = 0
        for num in nums:
            answer ^= num
            
        return answer
```

### Explanation:
TLDR: This solution relies on basic number theory. If every element is repeated twice except for one, the answer is the sum of the set of all nums, multiplied by two, then subtracted from the actual sum of the array.

## Solution:
```Python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        total = 0
        expected = 0
        for num in nums:
            total += num
            
        for num in set(nums):
            expected += num * 2
            
        return expected - total
```
