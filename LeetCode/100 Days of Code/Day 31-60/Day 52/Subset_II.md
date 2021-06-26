# [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

## Solutions

### Solution 1

```
function getSubsets(nums, index, list, sublist, pushed){
    let temp = JSON.parse(JSON.stringify(sublist))
    temp.sort(function(a,b){return a-b})
    if(!pushed[JSON.stringify(temp)]) {
        list.push(temp)
        pushed[JSON.stringify(temp)] = true
    }
    
    for(let i=index+1; i<nums.length; i++){
        sublist.push(nums[i])
        getSubsets(nums, i, list, sublist, pushed)
        sublist.pop()
    }
}

var subsetsWithDup = function(nums) {
    let list = []
    let pushed = {}
    getSubsets(nums, -1, list, [], pushed)
    return list
};
```