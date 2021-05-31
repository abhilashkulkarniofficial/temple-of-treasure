# [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

## Solutions

### Solution 1

```
var containsDuplicate = function(nums) {
    let contains = {}
    for(const x of nums){
        if(contains[x]) return true
        contains[x] = 1
    }
    return false
};
```