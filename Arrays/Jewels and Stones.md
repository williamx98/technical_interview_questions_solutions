# Jewels and Stones

[Question Link](https://leetcode.com/problems/jewels-and-stones/)  

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.  

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".  

### Explanation:
TLDR: make a set with the jewels that are given. Check each stones existence in the jewels set.

## Solution:
```Python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        jewels = set(J)
        
        answer = 0
        for s in S:
            if s in jewels:
                answer = answer + 1
                
        return answer     
```
