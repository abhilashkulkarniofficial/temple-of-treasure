# [Find K Closest Elements]()

## Solutions

### Solution 1

```
var findClosestElements = function(arr, k, x) {
    let dist = []
    for(let i=0; i<arr.length; i++){
        dist.push([arr[i],Math.abs(arr[i]-x)])
    }
    dist.sort(function(a,b){return a[1]-b[1]})
    // console.log(dist)
    let ret = []
    for(let i=0; i<k; i++){
        ret.push(dist[i][0])
    }
    return ret.sort(function(a,b){return a-b})
};
```