# Fair Candy Swap  
### Rating: [3/5] Convoluted setup but the solution helps train your mind to see arrays differently.

[Question Link](https://leetcode.com/problems/fair-candy-swap/)  

Alice and Bob have candy bars of different sizes: A[i] is the size of the i-th bar of candy that Alice has, and B[j] is the size of the j-th bar of candy that Bob has.  

Since they are friends, they would like to exchange one candy bar each so that after the exchange, they both have the same total amount of candy.  (The total amount of candy a person has is the sum of the sizes of candy bars they have.). 

Return an integer array ans where ans[0] is the size of the candy bar that Alice must exchange, and ans[1] is the size of the candy bar that Bob must exchange.  

If there are multiple answers, you may return any one of them.  It is guaranteed an answer exists.  

### Explanation:
TLDR: The target sum for each person is going to the average of (sum(Alice) + sum(B)) / 2. It should be clear as to why. Store the Bob's elements in a set. Iterate through the set and identify if a possible swap can occur by first "taking out" (subtracting) the current item in evaluation from the origin sum(Alice) - this will give you a target value, a value that if added to the temp sum(Alice) would equal the target sum. This target value should be looked for in the set(Bob). 


## Solution:
```Python
class Solution(object):
    def fairCandySwap(self, A, B):
        """
        :type A: List[int]
        :type B: List[int]
        :rtype: List[int]
        """
        alicesGivenTotal = 0
        setOfAlicesBars = set()
        bobsGivenTotal = 0
        setOfBobsBars = set()
        
        for oneOfAlicesBars in A:
            alicesGivenTotal = alicesGivenTotal + oneOfAlicesBars
            setOfAlicesBars.add(oneOfAlicesBars)
        
        for oneOfBobsBars in B:
            bobsGivenTotal = bobsGivenTotal + oneOfBobsBars
            setOfBobsBars.add(oneOfBobsBars)
            
        # fairValue is the target total for Alice and Bob indivdually.
        # i.e its the average of all the candy bars
        fairValue = (alicesGivenTotal + bobsGivenTotal)//2
        
        for oneOfAlicesUniqueBars in setOfAlicesBars:
            aliceWithoutOneOfHerBars = alicesGivenTotal - oneOfAlicesUniqueBars
            
            neededFromBob = fairValue - aliceWithoutOneOfHerBars

            if neededFromBob in setOfBobsBars:
                return [oneOfAlicesUniqueBars, neededFromBob]
```
