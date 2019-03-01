# Find All Numbers Disappeared in an Array  
## Rating: [3/5] Important trick of using the values themselves to mark certain indexes as used.

[Question Link](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)  

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.  

Find all the elements of [1, n] inclusive that do not appear in this array.  

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.  

##### Constraints:

### Explanation:
TLDR: Use the value at each index to mark the index indicated by the value as seen. The index of the remaining elements that are not negative should be appended to your answer.

## Solution:
```Python
class Solution(object):
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        answer = []
        for i in xrange(len(nums)):
            index = abs(nums[i]) - 1
            nums[index] = -abs(nums[index])

        for i in xrange(len(nums)):
            if nums[i] > 0:
                answer.append(i + 1)
                
        return answer
```
