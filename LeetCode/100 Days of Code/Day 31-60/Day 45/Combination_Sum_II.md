# [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)

## Solutions

### Solution 1

```
function ifExists(list, arr){
    for(const x of list){
        if(JSON.stringify(arr) === JSON.stringify(x)) return true
    }
    return false
}

function sum(candidates, index, target, sublist, list){
    
    for(let i=index+1; i<candidates.length; i++){
        sublist.push(candidates[i])
        let temp = sublist.reduce(function(a,b){return a+b})
        if(temp===target){
            let x = JSON.parse(JSON.stringify(sublist))
            x.sort(function(a,b){return a-b})
            if(!ifExists(list, x)) list.push(x)
        }else if(temp < target){
            sum(candidates, i, target, sublist, list)
        }
        sublist.pop()
    }
    return
}

var combinationSum2 = function(candidates, target) {
    let list = []
    sum(candidates, -1, target, [], list)
    // console.log(list)
    return list
};
```