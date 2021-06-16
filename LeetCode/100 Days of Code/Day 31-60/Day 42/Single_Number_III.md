# [260. Single Number III](https://leetcode.com/problems/single-number-iii/)

## Solutions

### Solution 1

```
var singleNumber = function(nums) {
    nums.sort(function(a,b){return a-b})
    console.log(nums)
    let ret = []
    for(let i=0; i<nums.length; i++){
        if(nums[i]===nums[i+1]){
            i++
        }else{
            ret.push(nums[i])
        }
    }
    return ret
};
```

TC: O(nlogn) + O(n)
SC: O(1)