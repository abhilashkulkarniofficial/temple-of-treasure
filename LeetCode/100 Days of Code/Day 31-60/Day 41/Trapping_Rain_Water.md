# [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

## Solutions

### Solution 1

Brute force approach


### Better solution

Using prefix-max and suffix-max arrays

```
var trap = function(height) {
    let prefix = []
    let suffix = []
    let max = 0
    for(let i=0; i<height.length; i++){
        if(max<height[i]) max = height[i]
        prefix.push(max)
    }
    
    max = 0
    for(let i=height.length-1; i>=0; i--){
        if(max<height[i]) max = height[i]
        suffix.push(max)
    }
    
    suffix.reverse()
    let res = 0
    for(let i=0; i<height.length; i++){
        res += Math.min.apply(Math,[prefix[i],suffix[i]]) - height[i]
    }
    return res
};
```

TC: O(n) + O(n) + O(n) = O(3n)
SC: O(2n)

### Optimal Solution

```
var trap = function(height) {
    let left = 0
    let leftmax = 0
    let right = height.length-1
    let rightmax = 0
    let res = 0
    
    while(left <= right){
        if(height[left]<=height[right]){
            if(height[left] >= leftmax) leftmax = height[left]
            else res += leftmax - height[left]
            left++
        }else{
            if(height[right] >= rightmax) rightmax = height[right]
            else res += rightmax - height[right]
            right--
        }
    }
    
    return res
};
```

TC: O(n)
SC: O(1)