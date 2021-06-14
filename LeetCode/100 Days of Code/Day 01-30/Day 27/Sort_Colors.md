# [75. Sort Colors](https://leetcode.com/problems/sort-colors/)

## Solutions

### Solution 1

Using 3 pointers
```
var sortColors = function(nums) {
    let one = 0
    let two = 0
    let len = nums.length
    while(len){
        let num = nums.pop()
        if(!num){
            nums.splice(0,0,0)
            one++
            two++
        }else if(num===1){
            nums.splice(one,0,1)
            two++
        }else{
            nums.splice(two,0,2)
        }
        len--
    }
    
    
};
```
