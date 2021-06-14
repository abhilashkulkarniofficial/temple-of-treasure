# [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

## Solutions

### Solution 1

```
var findDisappearedNumbers = function(nums) {
    let len = nums.length
    for(let i=0; i<len; i++){
        if(!nums.includes(i+1)){
            nums.push(i+1)
        }
    }
    return nums.slice(len,nums.length)
};
```