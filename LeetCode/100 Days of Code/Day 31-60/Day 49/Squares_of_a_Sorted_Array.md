# [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

## Solutions

### Solution 1

```
var sortedSquares = function(nums) {
    for(var x in nums){
        nums[x] = Math.pow(nums[x],2)
    }
    return nums.sort(function(a,b){return a-b})
};
```