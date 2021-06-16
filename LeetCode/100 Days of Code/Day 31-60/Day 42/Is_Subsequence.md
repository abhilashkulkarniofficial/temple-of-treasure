# [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)

## Solutions

### Solution 1

```
var isSubsequence = function(s, t) {
    let i=0
    let j=0
    while(j<t.length){
        if(s[i]===t[j]){
            i++
        }
        j++
    }
    return i===s.length
};
```

TC: O(n)
SC: O(1)