# [268. Missing Number](https://leetcode.com/problems/missing-number/)

## Solutions

### Solution 1

```
var missingNumber = function(nums) {
    return (nums.length*(nums.length+1)/2)-nums.reduce((a,b) => a+b)
};
```
