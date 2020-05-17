# Intersection of Two Arrays II  

## Rating: [4/5] Good question. Somewhat convoluted solution

[Question Link](https://leetcode.com/problems/intersection-of-two-arrays-ii/)  

Given two arrays, write a function to compute their intersection.  

### Explanation:
TLDR: 

## Solution:
### Assumes nums1 and nums2 are not sorted
```Python
class Solution(object):
    def intersect(self, nums1, nums2):

        nums1Counts = {}
        answer = []

        for num in nums1:
            nums1Counts[num] = nums1Counts.get(num, 0) + 1

        for num in nums2:
            if num in nums1Counts and nums1Counts[num] > 0:
                answer.append(num)
                nums1Counts[num] -= 1

        return answer
```

## Solution:
### Assumes nums1 and nums2 have already been sorted
```Python
class Solution(object):
    def intersect(self, nums1, nums2):        
        # nums1 = sorted(nums1)
        # nums2 = sorted(nums2)
        nums1Iterator = 0
        nums2Iterator = 0
        answer = []

        while nums1Iterator < len(nums1) and nums2Iterator < len(nums2):
            if nums1[nums1Iterator] > nums2[nums2Iterator]:
                nums2Iterator += 1
            elif nums1[nums1Iterator] < nums2[nums2Iterator]:
                nums1Iterator += 1
            else:
                answer.append(nums1[nums1Iterator])
                nums1Iterator += 1
                nums2Iterator += 1

        return answer
```