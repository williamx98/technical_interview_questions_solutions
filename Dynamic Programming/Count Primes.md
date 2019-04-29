# Count Primes  

[Question Link](https://leetcode.com/problems/count-primes/)  

Count the number of prime numbers less than a non-negative number, n.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution:
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n < 2:
            return 0
        
        s = [1] * n
        s[0] = 0
        s[1] = 0
        total = n - 2

		# Dynamic Programming Esque Solution
		# Once we find a prime number, set all multiples of that number to be not prime
		# For example:
		# 2 is prime. 4, 8, 10, 12... is not. So starting at 2 * 2, incrementing by 2, set all those 
		# numbers to not prime (0)
        
        for i in xrange(2, int(n ** 0.5) + 1):
            if s[i] == 1:
                for j in xrange(i * i, n, i):
                    # s[j] will be 0 if it has been seen before so then total won't move. 
                    total -= s[j]
                    s[j] = 0

        return total
```