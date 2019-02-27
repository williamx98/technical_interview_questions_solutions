# Rotate Array  

[Question Link](https://leetcode.com/problems/rotate-array/)  

Given an array, rotate the array to the right by k steps, where k is non-negative.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:
If the length of the array is even, the cyclical swap will go on forever. Keep conditions before the swap, once the swap hits those conditions, start at the next index.

## Solution:
```Python
class Solution(object):
    def rotate(self, nums, k):
        n = len(nums)
        k = k % n
        if k == 0:
            return
        
        i = 0
        count = n
        
        while count > 0:
            pos = (i + k) % n
            curr = nums[pos]
            nums[pos] = nums[i]
            count -= 1
            j = pos
            
            while j != i and count > 0:
                pos = (j + k) % n
                temp = nums[pos]
                nums[pos] = curr
                curr = temp
                j = pos
                count -= 1
                
            i += 1
```