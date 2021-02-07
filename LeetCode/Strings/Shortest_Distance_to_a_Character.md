# [Shortest Distance to a Character](https://leetcode.com/problems/shortest-distance-to-a-character/)

Given a string s and a character c that occurs in s, return an array of integers answer where answer.length == s.length and answer[i] is the shortest distance from s[i] to the character c in s.

### Examples

```
Input: s = "loveleetcode", c = "e"
Output: [3,2,1,0,1,0,0,1,2,2,1,0]

Input: s = "aaab", c = "b"
Output: [3,2,1,0]
```

## My Solution

```
/**
 * @param {string} s
 * @param {character} c
 * @return {number[]}
 */
var shortestToChar = function(s, c) {
    let charIndex = []
    for(let i=0; i<s.length; i++){
        if(s[i]===c){
            charIndex.push(i)
        }
    }
    let retArray = []
    for(let i=0; i<s.length; i++){
        if(s[i]===c){
            retArray.push(0)
        }else{
            let dist = s.length
            for(let j=0; j<charIndex.length; j++){
                if(dist>Math.abs(i-charIndex[j])){
                    dist = Math.abs(i-charIndex[j])
                }
            }
            retArray.push(dist)
        }
    }
    return retArray
};
```
