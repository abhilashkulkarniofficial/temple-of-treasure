# [39. Combination Sum](https://leetcode.com/problems/combination-sum/)

## Solutions

### Solution 1

```
function sum(candidates, index, target, sublist, list){
    
    for(let i=index; i<candidates.length; i++){
        sublist.push(candidates[i])
        let temp = sublist.reduce(function(a,b){return a+b})
        if(temp===target){
            let x = JSON.parse(JSON.stringify(sublist))
            list.push(x)
        }else if(temp < target){
            sum(candidates, i, target, sublist, list)
        }
        sublist.pop()
    }
    return
}

var combinationSum = function(candidates, target) {
    let list = []
    sum(candidates, 0, target, [], list)
    console.log(list)
    return list
};
```