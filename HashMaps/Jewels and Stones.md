# Jewels and Stones

[Question Link](https://leetcode.com/problems/jewels-and-stones/)  

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.  

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".  

##### Constraints:

### Explanation:
TLDR: make a hashmap with the stones that are given. Use the jewels that are given as a key to pull data from the hashmap of stones.

### Notes:


## Solution (Dict):
```Python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        J = list(J)
        S = list(S)
        total = 0
        
        sCount = {}
        for s in S:
            sCount[s] = sCount[s] + 1 if s in sCount else 1
        
        for j in J:
            if j in sCount:
                total += sCount[j]
        
        return total        
```

## Solution (Array):
```Python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        J = list(J)
        S = list(S)
        total = 0
        
        sCount = [0] * 256
        for s in S:
            sCount[ord(s)] += 1
        
        for j in J:
            total += sCount[ord(j)]
        
        return total
```