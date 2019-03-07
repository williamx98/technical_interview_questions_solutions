# Merge Sorted Array  

[Question Link](https://leetcode.com/problems/merge-sorted-array/)  

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.  

Note:  

The number of elements initialized in nums1 and nums2 are m and n respectively.  
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        insertPoint = len(nums1) - 1
        pointer1 = m - 1
        pointer2 = n - 1
        
        while pointer1 >= 0 or pointer2 >= 0:
            if pointer1 >= 0 and (pointer2 < 0 or nums1[pointer1] > nums2[pointer2]):
                nums1[insertPoint] = nums1[pointer1]
                pointer1 = pointer1 - 1
            else:
                nums1[insertPoint] = nums2[pointer2]
                pointer2 = pointer2 - 1
            
            insertPoint = insertPoint - 1
```