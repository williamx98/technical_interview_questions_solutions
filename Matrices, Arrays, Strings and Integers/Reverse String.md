# Reverse String

[Question Link](https://leetcode.com/problems/reverse-string/)  

Write a function that reverses a string. The input string is given as an array of characters char[].  

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.  

You may assume all the characters consist of printable ascii characters.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:

## Solution:
```Python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: void Do not return anything, modify s in-place instead.
        """
        return s[::-1]
```

## Solution:
```Python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: void Do not return anything, modify s in-place instead.
        """
        left = 0
        right = len(s) - 1
        
        while left <= right:
            temp = s[left]
            s[left] = s[right]
            s[right] = temp
            
            left += 1
            right -= 1
```