# Merge Sorted Array  

### Rating: [5/5] Good intro into array manipulation. 

[Question Link](https://leetcode.com/problems/merge-sorted-array/)  

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.  

Note:  

The number of elements initialized in nums1 and nums2 are m and n respectively.  
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.  

### Explanation:
TLDR: use two pointers to evaluate only 1 item from each array at a time. Since the arrays are sorted, we can traverse backwards and insert backwards.

Note: This is important to know for doing merge-sort

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

        # we are inserting at the end of nums1
        insertPoint = m + n - 1
        nums1Pointer = m - 1
        nums2Pointer = n - 1
        
        # while we have elements left to insert
        while nums1Pointer >= 0 or nums2Pointer >= 0:
            # if we still have items in nums1
            # AND
            # (if there are no items left in nums2 or if nums1 pointer has a larger value)
            if nums1Pointer >= 0 and (nums2Pointer < 0 or nums1[nums1Pointer] > nums2[nums2Pointer]):
                nums1[insertPoint] = nums1[nums1Pointer]
                nums1Pointer = nums1Pointer - 1
            else:
                nums1[insertPoint] = nums2[nums2Pointer]
                nums2Pointer = nums2Pointer - 1
            
            insertPoint = insertPoint - 1
```