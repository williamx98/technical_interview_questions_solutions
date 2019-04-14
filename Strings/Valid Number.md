# Valid Number   

[Question Link](https://leetcode.com/problems/valid-number/)  

Validate if a given string can be interpreted as a decimal number.  

### Explanation:
TLDR: On every character, only a certain subset of characters are allowed to occur next. The next subset of characters are determined based on the current character's type. This uses a method called DFA, deterministic finite automaton.

The underlying algorithm for RegExp uses DFA.

While the only character seen is a space, then only a space, a sign, a digit or a decimal point can follow.  
Following a sign, only a digit or decimal point can follow.  
Following a digit, only another digit, e, or a blank.  

The first consecutive blanks will be 'ignored' by not changing the initial state. i.e 10 spaces or 1 space won't change the initial state.  
The following spaces after a non-space character is seen will be regarded as the 'last' state i.e any other non-space characters following the current space will invalidate the number.  

## Solution:
```Python
class Solution(object):
    def isNumber(self, s):
        state = [{}, 
              {'blank': 1, 'sign': 2, 'digit':3, '.':4}, 
              {'digit':3, '.':4},
              {'digit':3, '.':5, 'e':6, 'blank':9},
              {'digit':5},
              {'digit':5, 'e':6, 'blank':9},
              {'sign':7, 'digit':8},
              {'digit':8},
              {'digit':8, 'blank':9},
              {'blank':9}]
        currentState = 1
        for c in s:
            if c >= '0' and c <= '9':
                c = 'digit'
            if c == ' ':
                c = 'blank'
            if c in ['+', '-']:
                c = 'sign'
            if c not in state[currentState].keys():
                return False
            currentState = state[currentState][c]
        if currentState not in [3,5,8,9]:
            return False
        return True
```
