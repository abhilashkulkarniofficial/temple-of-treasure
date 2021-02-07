# [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

### Examples

```
Input: x = 121
Output: true

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

Input: x = -101
Output: false
```

## My solution

```
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if(x<0) return false
    if(x<10) return true
    x = ""+x
    let front = 0
    let end = x.length -1
    while(front < end){
            front++
            end--
        }else{
            return false
        }
    }
    return true
};
```
