# [169. Majority Element](https://leetcode.com/problems/majority-element/)

## Solutions

### Solution 1

```
var majorityElement = function(nums) {
    let hash = {}
    for(let x of nums){
        if(!hash[x]) hash[x] = 1
        else hash[x]++
    }
    return Object.keys(hash)[Object.values(hash).indexOf(Math.max.apply(Math,Object.values(hash)))]
};
```