# Intersection of Two Arrays II  

[Question Link](https://leetcode.com/problems/intersection-of-two-arrays-ii/)  

Given two arrays, write a function to compute their intersection.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def intersect(self, nums1, nums2):
        
        nums1 = sorted(nums1)
        nums2 = sorted(nums2)
        pt1 = 0
        pt2 = 0
        res = []

        while pt1 < len(nums1) and pt2 < len(nums2):
            if nums1[pt1] > nums2[pt2]:
                pt2 += 1
            elif nums1[pt1] < nums2[pt2]:
                pt1 += 1
            else:
                res.append(nums1[pt1])
                pt1 += 1
                pt2 += 1

        return res
```