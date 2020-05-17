# Array Partition I
### Rating: [2/5] Some-what convoluted question. Good for practicing breaking down logic.
[Question Link](https://leetcode.com/problems/array-partition-i/)  

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.    

### Explanation:
TLDR: Sort and add every other one.

For every pair we generate, we need to maximize the value of ```min(a, b)```. 

When generate 1 pair, we can maximize the value of ```min(a, b)``` by using ```min(max(nums), second_max(nums))```
where ```max()``` returns the largest unpaired number in nums and ```second_max(nums)``` returns the *second* largest unpaired number in nums.

We know its not possible to use the largest unpaired value because for the ```min``` function to be valid, there **must** be a value that is smaller than the largest unpaired value. That means, the largest possible value for ```min(a, b)``` is to use 
```min(max(nums), second_max(nums))```.

Since the largest and second largest unpaired numbers would be next to each other when sorted in order, we can infer that the solution is to sort the array and add every other number starting from index 0.

## Solution:
```Python
class Solution(object):
    def arrayPairSum(self, nums):
        nums.sort()
        total = 0
        for index in xrange(0, len(nums), 2):
            total += nums[index]
            
        return total
```
