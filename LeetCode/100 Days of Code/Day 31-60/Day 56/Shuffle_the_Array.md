# [1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

## Solutions

### Solution 1

```
var shuffle = function(nums, n) {
    let retArr = []
    for(let i=0; i<n; i++){
        retArr.push(nums[i])
        retArr.push(nums[n+i])
    }
    return retArr
};
```

TC: O(n)
SC: O(n)