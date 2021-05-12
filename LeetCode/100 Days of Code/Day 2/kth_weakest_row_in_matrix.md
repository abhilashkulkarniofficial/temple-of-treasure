# [1337. The K Weakest Rows in a Matrix](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)

## Solutions

### Solution 1

```
var kWeakestRows = function(mat, k) {
    let strength = {}
    let returnarr = []
    for(let i=0; i<mat.length; i++){
        strength[i] = mat[i].reduce((a,b) => a+b)
    }
    strength = Object.entries(strength).sort((a,b) => a[1] - b[1] )
    for(let i=0; i<k; i++){
        returnarr.push(parseInt(strength[i][0]))
    }
    return returnarr
};
```
