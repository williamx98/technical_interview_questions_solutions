# String to Integer (atoi)    

[Question Link](https://leetcode.com/problems/string-to-integer-atoi/)  

Implement atoi which converts a string to an integer.  

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.  

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.  

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.  

If no valid conversion could be performed, a zero value is returned.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:

## Solution:
```Java
class Solution {
    public int myAtoi(String str) {
        int answer = 0;
        int sign = 1;
        int index = 0;
        
        // move past spaces
        while (index < str.length() && str.charAt(index) == ' ') {
            index += 1;
        }
        
        // edge case
        if (index >= str.length()) {
            return answer;
        }
        
        // move past signs
        if (str.charAt(index) == '-') {
            sign = -1;
            index += 1;
        } else if (str.charAt(index) == '+') {
            index += 1;
        }

        // move through all consecutive numbers
        while (index < str.length() && (str.charAt(index) >= '0' && str.charAt(index) <= '9')) {
            int prev = answer;
            answer = answer * 10;
            answer = answer + (str.charAt(index) - '0');

            if (answer / 10 != prev) {
                if (sign == -1) {
                    return Integer.MIN_VALUE;
                } else {
                    return Integer.MAX_VALUE;
                }
            }
            index += 1;
        }
        
        return sign * answer;
    }
}
```

## Solution:
```Python
class Solution(object):
    def myAtoi(self, str):
        arr = list(str)
        state = [{},
                {' ': 1, '+': 2, '-': 2, 'digit': 2},
                {'digit': 2}]
            
        currState = 1
        answer = 0
        sign = 1
        index = 0
        while index < len(str):
            char = arr[index]
            
            if char >= '0' and char <= '9':
                answer = answer * 10
                answer += ord(char) - ord('0')
                char = 'digit'
                
            if currState == 1 and char == '-':
                sign = -1
            
            if char not in state[currState].keys():
                break

            if sign * answer < -2147483648:
                return -2147483648
                
            if sign * answer > 2147483647:
                return 2147483647
                
            currState = state[currState][char]
            index = index + 1
                
        return sign * answer
```