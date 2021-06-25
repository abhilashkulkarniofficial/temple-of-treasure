# [78. Subsets](https://leetcode.com/problems/subsets/)

## Solutions

### Solution 1

```
function getSubsets(nums, index, list, sublist){
    
    list.push(JSON.parse(JSON.stringify(sublist)))
    
    for(let i=index+1; i<nums.length; i++){
        sublist.push(nums[i])
        getSubsets(nums, i, list, sublist)
        sublist.pop()
    }
}

var subsets = function(nums) {
    let list = []
    getSubsets(nums, -1, list, [])
    return list
};
```