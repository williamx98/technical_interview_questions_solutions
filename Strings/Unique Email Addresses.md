# Unique Email Addresses

[Question Link](https://leetcode.com/problems/unique-email-addresses/)  

Every email consists of a local name and a domain name, separated by the @ sign.  

For example, in alice@leetcode.com, alice is the local name, and leetcode.com is the domain name.  

Besides lowercase letters, these emails may contain '.'s or '+'s.  

If you add periods ('.') between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.  For example, "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.  (Note that this rule does not apply for domain names.)  

If you add a plus ('+') in the local name, everything after the first plus sign will be ignored. This allows certain emails to be filtered, for example m.y+name@email.com will be forwarded to my@email.com.  (Again, this rule does not apply for domain names.)  

It is possible to use both of these rules at the same time.  

Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails?  
### Explanation:
TLDR: Use a set to eliminate duplicated copies of and keep a single copy of all emails. Return the length of the set

## Solution:
```Python
class Solution(object):
    def numUniqueEmails(self, emails):
        """
        :type emails: List[str]
        :rtype: int
        """
        answer = set();
        for email in emails:
            split = email.split("@")
            
            local = split[0]
            domain = split[1]
            
            local = local.split("+")[0]
            local = local.replace(".", "")
            
            newEmail = local + "@" + domain
            
            answer.add(newEmail)
            
        return len(answer)  
```
