# [566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)

## Solutions

### Solution 1

```
var matrixReshape = function(mat, r, c) {
    let m = mat.length
    let n = mat[0].length
    if(m*n !== r*c) return mat
    let all = []
    for(let i=0; i<m; i++){
        for(let j=0; j<n; j++){
            all.push(mat[i][j])
        }
    }
    let retArr = []
    let k=0
    for(let i=0; i<r; i++){
        let x = []
        for(let j=0; j<c; j++){
            x.push(all[k])
            k++
        }
        retArr.push(x)
    }
    return retArr
};
```

