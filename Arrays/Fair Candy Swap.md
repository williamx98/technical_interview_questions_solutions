# Fair Candy Swap  
### Rating: [4/5] Convoluted setup but the solution helps train your mind to see arrays differently.

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
        sumA = 0
        sumB = 0
        setB = set()
        
        for a in A:
            sumA = sumA + a
        
        for b in B:
            sumB = sumB + b
            setB.add(b)
            
        target = (sumA + sumB)//2
        
        for a in A:
        	# this is the tricky bit
        	# target represents the average of the two sets combined - i.e the target sum for set A and then set B individually. 
        	# for every item in a, you want to take that out of the sum of set A
        	# now that the set of A has the selected candy bar removed, you need to find the cooresponding bar in set B that can get A to the target
            need = (target - (sumA - a)) 

            if need in setB:
                return [a, need]
```
