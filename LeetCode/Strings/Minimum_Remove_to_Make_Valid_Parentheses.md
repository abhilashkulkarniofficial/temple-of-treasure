# [Minimum Remove to Make Valid Parentheses]()

Given a string s of '(' , ')' and lowercase English characters. 

Your task is to remove the minimum number of parentheses ( '(' or ')', in any positions ) so that the resulting parentheses string is valid and return any valid string.

Formally, a parentheses string is valid if and only if:

It is the empty string, contains only lowercase characters, or
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.


### Examples

```
Input: s = "lee(t(c)o)de)"
Output: "lee(t(c)o)de"
Explanation: "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.

Input: s = "a)b(c)d"
Output: "ab(c)d"

Input: s = "))(("
Output: ""
Explanation: An empty string is also valid.

Input: s = "(a(b(c)d)"
Output: "a(b(c)d)"
```

## My Solution:

```
/**
 * @param {string} s
 * @return {string}
 */
function removeInvalid(s, reverse){
    let complement = {'(':')',')':'('}
    let s1 = '('
    let s2 = ')'
    if(reverse){
        s1 = ')'
        s2 = '('
    }
    let stack = []
    let retString = ""
    let len = s.length
    for(let i=0; i<len; i++){
        // console.log(s[i])
        if(s[i] === s1){
            if(i===len-2 && s[i+1]===s2){
                retString+=s.substring(i,len)
                i++
            }else if(i===len-2 && s[i+1]===s1){
                i++
            }else{
                stack.push(s[i])
                retString+=s[i]
            }
            
        }else if(s[i] === s2 && s[i] === complement[stack.pop()]){
            retString+=s[i]
        }else if(!Object.keys(complement).includes(s[i])){
            retString+=s[i]
        }
        // console.log(retString)
    }

    return retString
}

var minRemoveToMakeValid = function(s) {
    s = removeInvalid(s, false)
    console.log(s)
    s = removeInvalid(s.split('').reverse().join(''), true)
    console.log(s)

    return s.split('').reverse().join('')
};

```
