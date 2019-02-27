# Find All Duplicates in an Array  

[Question Link](https://leetcode.com/problems/find-all-duplicates-in-an-array/)  

Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.  

Find all the elements that appear twice in this array.  

Could you do it without extra space and in O(n) runtime?  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def findDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        answer = []
        for num in nums:
            index = abs(num) - 1
            if nums[index] < 0:
                answer.append(index + 1)
            else:
                nums[index] = -abs(nums[index])
                
        return answer
```