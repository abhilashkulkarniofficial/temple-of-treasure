# [Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)

Given a string S, we can transform every letter individually to be lowercase or uppercase to create another string.

Return a list of all possible strings we could create. You can return the output in any order.

### Examples

```
Input: S = "a1b2"
Output: ["a1b2","a1B2","A1b2","A1B2"]

Input: S = "3z4"
Output: ["3z4","3Z4"]

Input: S = "12345"
Output: ["12345"]

Input: S = "0"
Output: ["0"]
```

## My Solution

```
/**
 * @param {string} S
 * @return {string[]}
 */
let arr = []

function solve(s, index, temp){
  if(index===s.length){
    arr.push(temp)
    return 
  }

  solve(s,index+1,temp+s[index])
  if(s[index] >= 'a' && s[index] <= 'z'){
         let x = s[index].toUpperCase();
         solve(s, index + 1, temp + x);
      }
      else if (s[index] >= 'A' && s[index] <= 'Z'){
         let x = s[index].toLowerCase();
         solve(s, index + 1, temp + x);
      }
}

var letterCasePermutation = function(S) {
    arr=[]
    solve(S, 0, "")
    return arr
};
```

[Resource](https://www.tutorialspoint.com/letter-case-permutation-in-cplusplus)
