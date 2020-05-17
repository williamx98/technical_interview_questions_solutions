# Next Greater Element I  

### Rating: [0/5] Terrible question. Would not recommend attempting to answer this. You will learn nothing.

[Question Link](https://leetcode.com/problems/next-greater-element-i/)  

You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.  

The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.  

### Explanation:
TLDR: Go backwards on nums. While there are items on the stack, pop until the current number is greater than the top of stack. Then associate the current number to the top of the stack (the element greater than it)

## Solution:
```Python
class Solution(object):
    def nextGreaterElement(self, findNums, nums):
        """
        :type findNums: List[int]
        :type nums: List[int]
        :rtype: List[int]
        """
        s = []
        answer = {}
        for num in nums[::-1]:
            while s and num > s[-1]:
                s.pop()
            
            greater = -1
            if s:
                greater = s[-1]
                
            answer[num] = greater
            s.append(num)
            
            
        a = []
        for num in findNums:
            a.append(answer[num])
        return a
```
