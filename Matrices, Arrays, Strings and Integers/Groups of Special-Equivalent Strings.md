# Groups of Special-Equivalent Strings  

[Question Link](https://leetcode.com/problems/groups-of-special-equivalent-strings/)  

You are given an array A of strings.  

Two strings S and T are special-equivalent if after any number of moves, S == T.  

A move consists of choosing two indices i and j with i % 2 == j % 2, and swapping S[i] with S[j].  

Now, a group of special-equivalent strings from A is a non-empty subset S of A such that any string not in S is not special-equivalent with any string in S.  

Return the number of groups of special-equivalent strings from A.  



##### Constraints:

### Explanation:
TLDR: isolate the even and odd indices. Then sort each sub group of the word. combine them into one big identity. Add them to set.

### Notes:


## Solution:
```Python
class Solution(object):
    def numSpecialEquivGroups(self, A):
        """
        :type A: List[str]
        :rtype: int
        """
        answer = set()
        for word in A:
            even = []
            odd = []
            for c in word[::2]:
                even.append(c)
            for c in word[1::2]:
                odd.append(c)
            even.sort()
            even.append(" ")
            odd.sort()
            even.extend(odd)
            even = "".join(even)
            answer.add(even)
        
        return len(answer)
```