# [15. 3Sum](https://leetcode.com/problems/3sum/)

## Solutions

### Not a solution

```
var threeSum = function(nums) {
    let set = []
    let x = []
    let hash = {}
    for(let i=0; i<nums.length; i++){
        if(!hash[nums[i]]) hash[nums[i]] = 1
        else hash[nums[i]]++
    }
    
    
    for(let i=0; i<nums.length-1; i++){
        hash[nums[i]]--
        for(let j=i+1; j<nums.length; j++){
            hash[nums[j]]--
            let sum = nums[i]+nums[j]
            if(hash[0-sum] && nums[i]!==nums[j] && nums[i]!==sum && nums[j]!==sum){
                console.log(nums[i],nums[j],sum)
            } 
            hash[nums[j]]++
        }
        hash[nums[i]]++
    }
    return set
};
```

TC: O(NxNxlog(M)) M is the time required to insert in the set
SC: O(M) + O(N)

### Solution

```
var threeSum = function(nums) {
    nums.sort(function(a,b){return a-b})
    let res = []
    for(let i=0; i<nums.length-2; i++){
        if(i===0 || (i>0 && nums[i]!==nums[i-1])){
            let low = i+1
            let high = nums.length-1
            let sum = 0 - nums[i]
            while(low < high){
                if(nums[low]+nums[high]===sum){
                    res.push([nums[low], nums[high], nums[i]])
                    
                    while(low < high && nums[low] === nums[low+1]) low++
                    while(low < high && nums[high] === nums[high-1]) high--
                    
                    low++
                    high--
                }else if(nums[low] + nums[high] < sum) low++
                else high--
            }
        }
    }
    console.log(res)
    return res
};
```

TC: O(nxn)
SC: Auxillary O(1)