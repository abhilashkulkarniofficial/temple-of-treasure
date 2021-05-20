# [494. Target Sum](https://leetcode.com/problems/target-sum/)

## Solutions

### Solution 1

```
let totalNumberOfWays = 0

function getSum(index, sum, nums, target){
    if(index === nums.length){
        if(sum === target) totalNumberOfWays++
        return
    }
    
    let pos = Math.abs(nums[index])
    let neg = -1 * pos
    
    getSum(index+1, pos+sum, nums, target)
    getSum(index+1, neg+sum, nums, target)
    
    return
}

var findTargetSumWays = function(nums, target) {
    totalNumberOfWays = 0
    getSum(0, 0, nums, target)
    return totalNumberOfWays
};
```