# [216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)

## Solutions

### Solution 1

```
function combination(n,k,index,list,sublist, nums){
    for(let i=index+1; i<nums.length; i++){
        sublist.push(nums[i])
        let sum = sublist.reduce(function(a,b){return a+b})
        if(sum===n && sublist.length===k){
            list.push(JSON.parse(JSON.stringify(sublist)))
        }else{
            combination(n,k,i,list,sublist,nums)
        }
        sublist.pop()
    }
    return
}

var combinationSum3 = function(k, n) {
    let nums = [1,2,3,4,5,6,7,8,9]
    let list = []
    combination(n, k, -1, list, [], nums)
    return list
};
```