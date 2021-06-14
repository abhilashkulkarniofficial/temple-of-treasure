# [136. Single Number](https://leetcode.com/problems/single-number/)

## Solutions

### Solution 1

```
var singleNumber = function(nums) {
    if(nums.length===1) return nums[0]
    nums.sort(function(a,b){return a-b})        // O(n)
    let i=0
    while(i<nums.length){       // O(n/2)
        if(nums[i]===nums[i+1]){
            i+=2
        }else{
            return nums[i]
        }
    }
};
```

TC: O(n)+O(n/2)
SC: O(1)


### Solution 2

Using XOR ^
```
var singleNumber = function(nums) {
    let result = 0
    for(let x of nums){
        result = result ^ x
    }
    return result
};
```