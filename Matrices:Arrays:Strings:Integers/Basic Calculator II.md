# Basic Calculator II  

[Question Link](https://leetcode.com/problems/basic-calculator-ii/)  

Implement a basic calculator to evaluate a simple expression string.  

The expression string contains only non-negative integers, +, -, \*, / operators and empty spaces . The integer division should truncate toward zero.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution:
    def calculate(self, s):
        if not s:
            return "0"
        stack, num, sign = [], 0, "+"
        
        for i in xrange(len(s)):
            if s[i].isdigit():
                num = num*10+ord(s[i])-ord("0")
            if s[i] in "*+-/" or i == len(s)-1:
                if sign == "-":
                    stack.append(-num)
                elif sign == "+":
                    stack.append(num)
                elif sign == "*":
                    stack.append(stack.pop()*num)
                else:
                    tmp = stack.pop()
                    if tmp//num < 0 and tmp%num != 0:
                        stack.append(tmp//num+1)
                    else:
                        stack.append(tmp//num)
                sign = s[i]
                num = 0
        return sum(stack)
```