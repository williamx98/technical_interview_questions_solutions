# Subdomain Visit Count

[Question Link](https://leetcode.com/problems/subdomain-visit-count/)  

A website domain like "discuss.leetcode.com" consists of various subdomains. At the top level, we have "com", at the next level, we have "leetcode.com", and at the lowest level, "discuss.leetcode.com". When we visit a domain like "discuss.leetcode.com", we will also visit the parent domains "leetcode.com" and "com" implicitly.  

Now, call a "count-paired domain" to be a count (representing the number of visits this domain received), followed by a space, followed by the address. An example of a count-paired domain might be "9001 discuss.leetcode.com".  

We are given a list cpdomains of count-paired domains. We would like a list of count-paired domains, (in the same format as the input, and in any order), that explicitly counts the number of visits to each subdomain.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def subdomainVisits(self, cpdomains):
        """
        :type cpdomains: List[str]
        :rtype: List[str]
        """
        hashtable = {}
        
        for domain in cpdomains:
            domain = domain.split(" ")
            visits = int(domain[0])
            domain = domain[1].split(".")
            
            currSub = []
            for sub in domain[::-1]:
                currSub.insert(0, sub)
                key = ".".join(currSub)
                if key in hashtable:
                    hashtable[key] += visits
                else:
                    hashtable[key] = visits
              
        answer = []
        for key in hashtable:
            item = str(hashtable[key]) + " " + key
            answer.append(item)
        return answer
```
