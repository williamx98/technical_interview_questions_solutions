# Sum of Two Integers  

[Question Link](https://leetcode.com/problems/sum-of-two-integers/)  

Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

##### Constraints:

### Explanation:
TLDR: 

### Notes:
The answer in python is kind of wacky and hopefully you won't ever encounter it. 

## Solution:
```Swift
class Solution {
    func getSum(_ a: Int, _ b: Int) -> Int {
        var answer = a
        var remaining = b
        while remaining != 0 {
            var carry = answer & remaining
            answer = answer ^ remaining
            remaining = carry << 1
        }
        
        return answer
    }
}
```