# Sum of Even Numbers After Queries

[Question Link](https://leetcode.com/problems/sum-of-even-numbers-after-queries/submissions/)  

We have an array A of integers, and an array queries of queries.  

For the i-th query val = queries[i][0], index = queries[i][1], we add val to A[index].  Then, the answer to the i-th query is the sum of the even values of A.  

(Here, the given index = queries[i][1] is a 0-based index, and each query permanently modifies the array A.)  

Return the answer to all queries.  Your answer array should have answer[i] as the answer to the i-th query.  

##### Constraints:

### Explanation:
TLDR: Calculate the total of even numbers before any queries. Update the toal of even numbers on every query based on how that query modified that index.

### Notes:
No need to recalculate the total of evens on every query by interating through the entire array.  

Don't forget to set the new value on every query.  

## Solution:
```Python
class Solution(object):
    def sumEvenAfterQueries(self, A, queries):
        """
        :type A: List[int]
        :type queries: List[List[int]]
        :rtype: List[int]
        """
        totalEvens = 0
        
        for a in A:
            if a % 2 == 0:
                totalEvens = totalEvens + a
            
        answer = []
        for q in queries:
            access = q[1]
            preValue = A[access]
            postValue = preValue + q[0]
            A[access] = postValue
        
            if preValue % 2 == 0:
                totalEvens = totalEvens - preValue
                
            if postValue % 2 == 0:
                totalEvens = totalEvens + postValue
            
            answer.append(totalEvens)
            
        return answer
```