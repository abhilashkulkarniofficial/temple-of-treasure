# [77. Combinations](https://leetcode.com/problems/combinations/)

## Solutions

### Solution 1

```
function combination(n,k,index,list,sublist){
    for(let i=index+1; i<n+1; i++){
        sublist.push(i)
        if(sublist.length===k){
            list.push(JSON.parse(JSON.stringify(sublist)))
        }else{
            combination(n,k,i,list,sublist)
        }
        sublist.pop()
    }
    return
}

var combine = function(n, k) {
    let list = []
    combination(n, k, 0, list, [])
    return list
};
```