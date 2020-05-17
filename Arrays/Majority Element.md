# Majority Element  

### Rating: [5/5] Good intro into arrays and number theory(?). Straight foward question, straight foward solution. Good advanced solution.

[Question Link](https://leetcode.com/problems/majority-element/)  

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.  

You may assume that the array is non-empty and the majority element always exist in the array.  

##### Constraints:

### Explanation:
TLDR: Sort the nums array. The majority element is guaranteed to be in the middle.


## Simple Solution:
```Python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums.sort()
        return nums[len(nums)//2]
```
### Explanation:
This seems somewhat complex but is actually very straight forward.

Pick the first element as a possible answer.
Everytime you see a value that matches the first element, increase the counter.  
Everytime you see a value that doesn't match the first element, decrease the counter.
When you reach zero on the counter, change the possible answer to the current value.

The possible answer will always be correct because the marjority element has the greatest count out of all the values in the array.

For example ```[2,2,3,3,3]```
```count``` will reach two by index ```1```
However, because there are three ```3```s, the possible answer will be set to ```3``` by index ```3```

For example ```[3,3,3,2,2]```
```count``` will reach 3 by index ```2```
However, because there are three ```3```s, the possible answer will not change from ```3``` because there are only two ```2```s so count can never be zero.

## Advanced Solution:
```Python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        possibleAnswer = nums[0]
        countOfPossibleAnswer = 0
        for num in nums:
            if countOfPossibleAnswer == 0:
                possibleAnswer = nums[i]
            
            if possibleAnswer == nums[i]:
                countOfPossibleAnswer += 1
            else:
                countOfPossibleAnswer -= 1
        return possibleAnswer
```