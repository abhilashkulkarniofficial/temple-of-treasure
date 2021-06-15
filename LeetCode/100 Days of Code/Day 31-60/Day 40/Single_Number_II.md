# [137. Single Number II](https://leetcode.com/problems/single-number-ii/)

## Solutions

### Solution 1

```
var singleNumber = function(nums) {
    if(nums.length===1) return nums[0]
    nums.sort(function(a,b){ return a>b?1:-1})
    let i=0
    while(i<nums.length){
        if(nums[i]===nums[i+1] && (nums[i+1]===nums[i+2])){
            i+=3
        }else{
            return nums[i]
        }
    }
};
```

TC: O(NlogN)+O(N/3)
SC: O(1)