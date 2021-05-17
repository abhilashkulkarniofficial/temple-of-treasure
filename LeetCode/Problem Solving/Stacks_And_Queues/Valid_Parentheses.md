# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

### Examples

```
Input: s = "()"
Output: true

Input: s = "()[]{}"
Output: true

Input: s = "(]"
Output: false

Input: s = "([)]"
Output: false

Input: s = "{[]}"
Output: true
```

## My solution

```
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let parentStack = []
    let complementObj = {'(':')','{':'}','[':']'}
    let index = 0
    while(index != s.length){
        let char = s[index]
        if(['(','[','{'].includes(char)){
            parentStack.push(char)
        }else if(char != complementObj[parentStack[parentStack.length -1]]){
            return false
        }else{
            parentStack.pop()
        }
        index++
    }
    if(parentStack.length == 0){
        return true
    }else{
        return false
    }
};
```
