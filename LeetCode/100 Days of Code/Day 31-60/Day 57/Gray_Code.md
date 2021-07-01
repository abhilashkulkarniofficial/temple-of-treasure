# [89. Gray Code](https://leetcode.com/problems/gray-code/)

## Solutions

### Solution 1

```
function getGreyBits(n){
    if(n===1){
        return ["0","1"]
    }
    
    let rres = getGreyBits(n-1)
    let mres = []
    for(let i=0; i<rres.length; i++){
        mres.push("0"+rres[i])
    }
    for(let i=rres.length-1; i>=0; i--){
        mres.push("1"+rres[i])
    }
    return mres
}

var grayCode = function(n) {
    let result = getGreyBits(n)
    result = result.map(val => parseInt(val, 2))
    return result
};
```

TC: O(n)
SC: O(1)