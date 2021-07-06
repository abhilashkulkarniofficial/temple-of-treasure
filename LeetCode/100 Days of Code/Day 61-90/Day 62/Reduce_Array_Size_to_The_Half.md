# [1338. Reduce Array Size to The Half](https://leetcode.com/problems/reduce-array-size-to-the-half/)

## Solutions

### Solution 1

```
var minSetSize = function(arr) {
    let map = {}
    let n = arr.length
    for(let i=0; i<n; i++){
        if(!map[arr[i]]) map[arr[i]] = 1
        else map[arr[i]]++
    }
    let temp = []
    let size = n
    let ret = 0
    for(const x in map){
        temp.push(map[x])
    }
    temp.sort(function(a,b){return b-a})
    console.log(temp)
    for(let i=0; i<temp.length; i++){
        console.log(size, ret)
        if(size <= parseInt(n/2)) break
        ret++
        size-=temp[i]
    }
    return ret
};
```